**Pyxlz: Managing Zynstra VM Lifecycles**

Pyxlz is Zynstra's main VM management tool, operating as a daemon on [[zhapcon]] and playing a vital role in managing VM lifecycles on the [[Zynstra IES]] (Infrastructure Edge System). It interacts with Xen through various means, including 'xl' and xenstore, to manage the states of both infrastructure and customer VMs. Pyxlz enables other services, like [[Zynstra Sync]], to participate in VM management using a system of state keys. Moreover, it supports essential features like dependency management and startup prioritization. The name "Pyxlz" is a shortened version of "PYthon XL Zynstra," reflecting its use of the [[libxenlight]] [[Xen]] library, which the 'xl' command is also named after.

The main code for Pyxlz is located in the `zynstra/Utilities/pyxlz` package on the Git repository (in the src folder). Additionally, there are some zhapcon-specific utilities in the `zynstra/Utilities/pyxlz-dom0` package. Although Pyxlz is often associated with zhapcon, it is installed on other VMs as well. For example, it is used on `znetdd` to notify zhapcon when OpenVSwitch interfaces are ready.

Pyxlz operates as a daemon under the `zynstra-pyxlzd.service` systemd service, with support from the `zynstra-pyxlzd-supervisor.service` to ensure smooth operation.

**[[How Pyxlz Works]]**

**[[Interacting with Pyxlz]]**

**[[Debugging Pyxlz]]**

[[Pyxlz Broadcaster]]