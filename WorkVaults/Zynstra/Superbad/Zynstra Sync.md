## Find

- repo - `startup/zynstra/Clustering/zdiskdd-clustering-components/src/zynstra_sync`
- zhapcon - `/usr/local/lib/python3.8/dist-packages/zynstra_sync`
- service - `zynstra-sync-vm-status.service`
- log - `/var/log/zynstra_sync/sync_xenstore_vm_status.log`

## Description

A `systemd` service on [[zhapcon]] which is used for automated VM management and forms a crucial part of our high availability implementation. Internally, the service watches the states of [[DRBD]] backed resources, using their states to makes decisions on ___ at the VM level.

The _"sync service"_ is the primary driver of the VM failover behavior (starting a VM on the other side should the original side becomes unavailable), as well as a good point of contact for more infrequent/edge-case scenarios, such as `split brain`.

The service manipulates VMs by modifying the `zdiskdd-blocks-ready` state key using [[Pyxlz]]. It can initiate or block a startup of a VM via setting this key to `RUN` / `SHUTDOWN` and, in tandem with other `state` keys, determines the overall `state` of the VM.

## Testing

The service is covered by an extensive number of unit tests, alongside the automated `OvernightHA` suite of tests, which emulate and test a variety of scenarios, on real servers, within a real context.

## Resources

- [Stack Overflow - What is "the sync service"?](https://stackoverflow.com/c/zynstra/questions/228)
- [Docusaurus - Sync Service](https://docs.dev.zynstra.com/docs/5.0/Startup/Infrastructure/Sync%20Service)
- Package `README.md` (somewhat out of date) - `zynstra/Clustering/zdiskdd-clustering-components/src/README.md`

[Home](https://git.dev.zynstra.com/zynstra/startup-wiki/-/wikis/Superbad-Team-Wiki/)