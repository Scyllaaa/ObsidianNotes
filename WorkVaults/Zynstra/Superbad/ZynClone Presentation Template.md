
# Title Slide
Welcome to the [[ZynClone]] Presentation
Purpose and Capabilities of ZynClone
### Slide 1: Introduction
Briefly introduce the ZynClone project.
Mention that ZynClone is designed to manage and create Xen virtual machine clones.
Highlight the key features of ZynClone:
- Online and offline Xen VM clones
- Network and peripheral lockdown for the clone or original VM
- Integration into the Zynstra noVNC console for access to the clone VM's console
- An interface enabling orchestration of cloning from within a guest VM
- Shared volume switching for data sharing between clone and original VM
- Mention the languages used for implementation: Bash, Python, and Powershell.
### Slide 2: Clone States
Explain the three clone states in the backend components:
running: The clone VM is running.
active: The clone VM is in an active configuration state, but not running. Network lockdowns on the original VM are enforced.
inactive: The clone configuration and VM volumes are still present but inactive, and network lockdowns on the original VM are disabled.

%%### Slide 3: Files & Directories
Explain the locations of ZynClone packages and scripts on the three managed SDS machines (zhapcon, znetdd, and zconsole).
Mention the changes in file locations from version 4.x to 5.1 onwards.%%
### Slide 4: Entry Control Script (vmclone)
Introduce the main entry control script, vmclone, located on zhapcon.
Describe the various modes and commands available in vmclone for managing clones.
Provide some basic vmclone command examples for creating, starting, stopping, and removing clones.
### Slide 5: Monitor Scripts
Explain the role of monitor scripts running on zhapcon, znetdd, and zconsole.
Describe the responsibilities of each monitor script:
clone_monitor on zhapcon: Publishes clone configuration into XenStore and applies frontend network lockdown.
clone_net_monitor on znetdd: Locks down the backend network using information from XenStore.
clone_console_monitor on zconsole: Provides a noVNC console for a clone using information from XenStore.
### Slide 6: Guest Orchestration
Discuss guest orchestration implemented in the clone_guest_orchestrator script.
Explain the purpose of guest orchestration, allowing original VMs to submit ZynClone commands for various clone-related functions.
Mention the use of XenStore for listening to changes in ZynClone XenStore keys.
### Slide 7: Configuration
Introduce the guest configuration files in /etc/xen/clone/guest directory on zhapcon.
Provide examples of key-value pairs in a guest config file.
Explain how clone configuration files are generated from a base config json and can be overridden per VM.
### Slide 8: Vif Masks
Describe how network lockdowns are controlled by Vif Mask values in ZynClone configuration.
Provide examples of different Vif Mask values and their effects on network lockdowns.
### Slide 9: Use Case: VM Diagnostics
Present a use case scenario for VM diagnostics using ZynClone.
Explain the steps for creating an online clone, investigating using noVNC console, and removing the clone.
### Slide 10: Debug Notes and Upgrades
Provide helpful debug notes, ensuring all monitor services are running, and how to view orchestrator logs.
Mention upgrade considerations, especially from versions prior to 5.1.
### Slide 11: Limitations
Discuss previous limitations with SDS versions prior to 5.1 and the manual workaround.
Highlight the current limitation with SPICE and Continuous Operations not being compatible.
### Slide 12: Conclusion
Summarize the purpose and capabilities of ZynClone.
Thank the audience for attending the presentation.
Encourage questions and discussion from the audience.
### Slide 13: Q&A
Open the floor for questions and answers.
Be prepared to address any inquiries from the audience.
### Slide 14: Thank You
Express gratitude to the audience for their time and attention.
Provide contact information or resources for further inquiries about ZynClone.