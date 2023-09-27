In case the `zstart` or `zstop` commands do not produce the expected effects, the following steps can be taken to debug:

1. Run `zstatus` to check the status of the relevant keys.
2. Inspect `/var/log/pyxlz-history.log` to confirm if the command was processed correctly by Pyxlz.
3. Check `journalctl -u zynstra-pyxlzd -xe` for any errors or traceback information.
