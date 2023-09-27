The uptime monitor records uptime information on each cluster and sends this information to the database where reports can be generated from the data.

The uptime monitor documents the start and end times of each IES boot cycle, along with the reasons for the cycle's termination. This documentation will primarily focus on the technical details of the service.

- Implemented in the [[Go|Go]] programming language.
- Uptime data is uploaded to [[CouchDB]] when the server is booted and every 6 hours thereafter.
- When uptime data upload to the database is unsuccessful the uptime monitor will wait 5 minutes before retrying, after 10 unsuccessful retries the upload will be skipped and upload will be attempted again in 6 hours.
- Any shutdown reasons are added to the shutdown reasons flags folder (`/var/log/uptime-monitor/shutdown_reasons`) and uploaded to the database on the next upload. Once uploaded to the database the shutdown reasons are deleted locally.
- If crash records in `/zynstra/config/pstore` indicate that the previous shutdown was caused by a crash then the crash reason is added to the shutdown reasons folder and uploaded to the database.
- Uptime data is updated locally on the [[IES]] every 30 seconds, the data is read from `/proc/uptime`. The local uptime record on the [[IES]] is located in `/var/log/uptime-monitor/uptime_heartbeat`, the directory contains files representing each boot cycle. The name of the file is start epoch of the boot cycle and the file contains the seconds ran during the boot. The contents of the file representing the current boot cycle is updated every 30 seconds with the new run seconds. When the server reboots, another boot cycle is created and updated.
- Last successful upload flag: `/var/log/uptime-monitor/last_successful_upload`. The modified time of this is updated to the time of the last successful upload. During uptime upload, all uptime data modified after this flag file was last modified is sent to the database in a request.
- Shutdown reasons are stored in `/var/log/uptime-monitor/shutdown_reasons`. Each reason is in the format `<reason>-<4 digits>`, for example `CONTROLLED-1234`, the digits at the enf of the reason are added to make each reason unique since if there are multiple reboots while couch connection is compromised then the reason would be overwritten. The modified time of each shutdown reason is used as the time the shutdown reason is added. The reason file is deleted once it has been successfully uploaded to the database.
## Configuration

A configuration file is located in `/zynstra/config/uptime_monitor_settings.json`. The configuration file is a JSON file containing the following fields:

- `DatabaseUploadHoursDuration`: How many hours between each uptime data upload to the database.
- `UptimeHeartbeatSecondsRun`: Data is from `/proc/uptime` every _n_ number of seconds as specified here.
- `NumOfRequestRetries`: How many database upload retries are made if an upload fails before skipping this upload and waiting for the next one.
- `WaitMinutesBeforeUploadRetry`: How many minutes before a retry if an upload to the database fails.

Restart the service for change to take effect - `systemctl restart uptime-monitor`

## Debug

- If a monitoring check shows CRIT or if there has been no uptime upload for a while, the problem is most likely caused by an ICP/DB network issue that's preventing uptime upload. Once the network problem is resolved, wait for up to 6 hours for the next uptime database upload to start, or restart the uptime-monitor service to trigger an upload attempt.
- Check the uptime monitor logs for details of common failures. Log location: `/var/log/uptime-monitor/uptimeMonitoringLogs.log`
- Check the monitoring check for more information.
- Check the systemd logs.
- Restart the service `systemctl restart uptime-monitor.service` to force new uptime upload and check logs for upload.
- Run the uptime monitor manually using command `/usr/local/bin/uptime-monitor` and check for error messages displayed. **NOTE:** The program will output nothing and appear to hang forever if there has been no errors since it will keep uploading to the database and updating local records.
- The uptime monitor may take up to 10 minutes from boot to upload to the database. This is due to the network services not being fully operational straight after a node has been booted.
## Useful locations

- Log on IES: `/var/log/uptime-monitor/uptimeMonitoringLogs.log`

# Metrics Database

Uptime data is sent to the database from the IES via a POST request and processed using CouchDB design documents. On CouchDB each cluster has a document in the metrics database which can be found at `https://<couch url>:6984/_utils/index.html#database/metrics/_all_docs`, each clusters uptime data document is of the following format:

```
{
    "_id": "cluster-0000-xxxx",
    "_rev": "<revision ID>",
    "type": "uptime",
    "store": "<store id>",
    "boot_cycles": [
        {
        "boot": 1673475018,
        "run": 892.21,
        "reasons": null
        },
        {
        "boot": 1673476831,
        "run": 2207159.35,
        "reasons": null
        }
    ]
}
```

### Database Fields

- The `boot` section of each boot cycle is the epoch when it was booted.
- The `run` section in each boot cycle contains the seconds in the boot cycle.

### Useful Information

- The last boot cycle is the current one and the `run` section is updated through an IES post request every 6 hours.
- The couch design documents for this database are located [here.](https://git.dev.zynstra.com/zynstra-dev/startup/-/tree/development/zynstra/Config/couchapp/src/metrics/uptime-data)

# Checkmk Monitoring Check

The monitoring check confirms that the last uptime data upload to the database is not longer than the scheduled upload time. There is a monitoring check which displays a `CRIT` alert when the uptime monitor has not uploaded for 7 hours. The uptime monitor sends data to the database every 6 hours, but an extra hour is added as a buffer if there is a temporary network issue.

A `CRIT` alert is also raised when there has been no upload to the database within 20 minutes from boot. The first uptime database upload from boot should be around 10 minutes from boot, so an extra 10 minute threshold is added. 

The monitoring check can be one of the following states:

`CRIT - Server has not begun to update the database - active since \<boot time>`

`CRIT - Time without upload exceeds threshold of 6 hours. Last update \<last uptime upload time>.`

`OK - Last upload to database was at \<last upload time>.`

`OK - Monitoring will begin after 20 minutes - active for \<server on time>.`

If monitoring is showing a CRIT state then resolve using techniques as described in the Debug section of the IES Uptime Monitor section of this documentation.

### Uptime Report Generator

The report generator is a Python script used to generate human readable reports from the uptime data on the database. Five different types of report can be generated, each report displays different information derived from the uptime data. Reports can be generated for clusters or stores on an individual basis or in any multiples as required. Reporting on dual edge stores starts from when there is data available for both clusters in the store. This is because if one cluster is patched before the other, store data will be incomplete until the latter cluster has the uptime monitor installed.

The reports are saved in a specified folder as CSV files.

#### Arguments:

**`--report_type`** - the type of uptime report required.

Options:

- **`uptime_percentage`** - uptime percentage for the past day, week, month, quarter and year. For stores the uptime is combined so the percentage uptime is per the store rather than the individual nodes.
- **`all_boot_cycles`** - the date and time of all instances where the cluster was shutdown and booted up again, alongside reason for the shutdown, e.g. controlled or uncontrolled.
- **`shutdown_events`** - date and time of all instances where the cluster was shutdown.
- **`boot_events`** - date and time of all instances where the cluster was booted up.
- **`uptime_percent_per_week`** - percentage uptime per week for every week in the past year.
- **`all`** - generate every type of report.

**`--save_directory`** - directory where the reports will be output to.

**`--stores`** and **`--clusters`** - these arguments are used to select the stores and/or clusters which will be included in the uptime report. These arguments are not mutually exclusive, and so can be used together. Moreover, they can be parameterized in the following ways:

- Selecting an individual cluster/store: `5` would produce a report of cluster/store 5.
- Selecting all: `*` selects all clusters or stores.

**`--remove_store_prefix`** - optional arg to remove the leading `S/s` from store numbers.

**Example command:** `python3 /usr/local/uptime-report-generation/generate_uptime_reports.py --report_type all --save_directory ./UPTIME_REPORTS --stores "00148"`

**Location on Zynops:** `/usr/local/bin/generate_uptime_reports.py`

### Automatically Generated Uptime Reports Available Via Zynops URL

Uptime reports are automatically generated on Zynops and are available to download through the URL `https://zynops-<MP>.zyntest12wan.local:8643/uptime-reports/`, either individually or together in a zipped file. The reports generated are specified using entries in the configuration file `/usr/local/uptime-report-generation/uptime_report_generation.cfg`. By default, there is a uptime report specification in the configuration file called `standard`, this generates all reports for all stores once every hour. The configuration file entry for the `standard` reports is the following:

```
{  "name": "standard",  "report_type": "all",  "stores": "*"}
```

The standard reports can be found in `https://zynops-<MP>.zyntest12wan.local:8643/uptime-reports/standard`. To add a new report, add a new JSON object to the list in the configuration file. When adding a new report specification, the `name` and `report_type` are both required and along with either a `stores` or `clusters` key to specify which clusters or stores to produce the reports on. These fields are the same as if you were generating a report manually as specified in the `Uptime Report Generator` section of this documentation. Once a new report specification has been added, either restart the service `systemctl restart uptime-report-generator` or wait up to an hour for the service to generate new reports so they are available to download.

Generated reports are saved under `/var/log/zynstra/uptime-reports`, this directory has been exposed using Apache2 in the configuration file `/etc/apache2/sites-available/api-viewer-ssl.conf`.

The logs for automatic uptime report generation are in `/var/log/generate_uptime_reports.log`.



https://docs.dev.zynstra.com/docs/5.2/Startup/Features/Uptime%20Monitor/#uptime-monitor-on-zhapcon 