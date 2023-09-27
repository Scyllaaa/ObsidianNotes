### Description
QEMU runs inside dom0/zhapcon for each zapp VM. The QEMU process sometimes needs a lot of CPU for a smooth VM experience.

Currently we hard-code the max VCPU of dom0 to 4 in the dom0.cfg grub. This is not enough when there are a lot of zapps (e.g. 20). This should be configurable via Couch and ideally based on the number of zapps the system has got configured.

The issue is somewhat related to that of zmonitor which also needs to scale: [#8247](https://git.dev.zynstra.com/zynstra-dev/startup/-/issues/8247 "zmonitor resource requirements increase with more zapps but we only have a static default resource allocation")
### Deez
### Comments
[James Dingwall](https://git.dev.zynstra.com/jdingwall) - Maintainer
This is a side effect of removing stubdoms. A stubdom is a xen domain and has its own dedicated vcpu assigned. Without the stubdom the qemu process runs in zhapcon and must contend with all other zhapcon processes on as many cpus as are assigned to zhapcon. (This is set in static boot time configuration for xen: `dom0_max_vcpus=4`)


### Summary 
- Currently hard-code max number of VCPU of dom0 to 4 in dom0.cfg grub
- Need to configure this via Couch, based on number of zapps system has configured.


### Findings
There exists a vpcu numbder stores at `core-node/_view_nodeRunsOnCPU` doc at "value/vcpu"

 xl list -l zapp-00