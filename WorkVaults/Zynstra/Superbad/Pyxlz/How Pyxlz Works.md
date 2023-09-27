Pyxlz determines the appropriate state for a VM by considering various factors. If the current state does not match the target state, Pyxlz takes corrective actions, such as starting or stopping the VM. Key factors considered by Pyxlz include:

1. The readiness of network interfaces in znetdd.
2. Whether the VM is currently being injected.
3. The readiness of any required DRBD devices.
4. Whether the VM has been manually stopped (using zstop) or stopped through the Zynstra Control Center (ZCC).
5. For Dual Edge systems, Pyxlz integrates with "the sync service" to prevent VMs from starting on both nodes simultaneously.
