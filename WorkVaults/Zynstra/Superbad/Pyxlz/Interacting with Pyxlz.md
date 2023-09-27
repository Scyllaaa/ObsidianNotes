The primary way to interact with Pyxlz is through its provided commands, which include:

- `zstart`: Sets the dom0-admin-state state key for a specific VM to "RUN," effectively starting the VM.
- `zstop`: Sets the dom0-admin-state state key for a specific VM to "SHUTDOWN," effectively stopping the VM.
- `zstart-all`: Starts all VMs on a given cluster by setting their dom0-admin-state to "RUN."
- `zstop-all`: Stops all VMs on a given cluster by setting their dom0-admin-state to "SHUTDOWN."
- `zstatus`: Displays state information for a specific VM.

The `zstart` and `zstop` commands can be resubmitted with the `-r` or `--resubmit` option to retry indefinitely until the desired changes take effect. Additionally, the `zstop` command supports the `-f` or `--force` option to forcefully stop a VM.