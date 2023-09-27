---
alias: CO, Continuous Operations
---

# Overview of Feature

The ZynClone project consists of a number of scripted components to orchestrate managing and creating Xen virtual machine clones. The following features are included:

- Online and offline Xen VM clones
- Network and peripheral lockdown for the clone or original VM
- Integration into the Zynstra noVNC console allowing access to the clone VM's console
- An interface enabling orchestration of cloning from within a guest VM
- Shared volume switching allows data sharing between clone and original VM

This project is written with Bash, Python and Powershell.

Main Components:

1. [[vmclone]]: The main entry control script responsible for managing Xen virtual machine clones. It handles creation, removal, starting, and stopping of clones and keeps track of clones using configuration files.

Sub-Components:

2. [[clone_monitor]]:
    - Location: Runs on zhapcon.
    - Responsibilities: Publishes clone configurations into XenStore and applies frontend network lockdown to clone/original VMs.
3. [[clone_net_monitor]]:
    - Location: Runs on znetdd.
    - Responsibilities: Locks down the backend network using information from XenStore.
4. [[clone_console_monitor]]:
    - Location: Runs on zconsole.
    - Responsibilities: Provides a noVNC console for a clone using information from XenStore.
5. [[clone_guest_orchestrator]]:
    - Location: Implemented in the clone_guest_orchestrator script.
    - Responsibilities: Allows the original VM to submit ZynClone commands for initiating new clones, cutovers, and other clone-related functions. It listens for changes to ZynClone XenStore keys.

Relationships:
- [[vmclone]] interacts with various components:
	- [[clone_monitor]]: vmclone writes clone configuration files, which clone_monitor publishes into XenStore for other VMs to access.
    - [[clone_net_monitor]]: vmclone sets network and peripheral lockdown values in configuration files, but clone_net_monitor applies the backend network lockdowns based on published XenStore information.
    - [[clone_console_monitor]]: vmclone sets up a noVNC console for clones, and clone_console_monitor gathers VNC port information from XenStore to provide access to the console.
- [[clone_guest_orchestrator]] interacts with vmclone and XenStore:
    - [[vmclone]] creates and manages clone configurations based on guest VMs' submissions to clone_guest_orchestrator.
    - [[clone_guest_orchestrator]] listens to changes in ZynClone XenStore keys and acts accordingly.

Note: The entire ZynClone project is written with Bash, Python, and Powershell, and it is designed to manage and create Xen virtual machine clones. The relationships mentioned above ensure proper coordination and functionality between the components to achieve the desired clone operations.