## Find

- service name - `systemctl status drbd.service`
- version info - `cat /proc/drbd`
- kernel module info - `modinfo drbd`

## Description

DRBD is used to keep the disks of specific VMs in sync between clusters. This enables quick failover or the live migration of VMs without any loss of data. Until `5.1`, in `Dual Edge`, only `CUSTOMER` VM types were backed by DRBD. However, some infrastructure VMs - such as the `k8s` quorum VM `zmuk8sq` - are starting to creep in.

Internally, DRBD works on a level of resources, and each VM can have multiple assigned depending on its needs. The interface which keeps the resources in sync is `Prepl0` (on `zhapcon`), and there's also a DRBD bridge from `5.0`.

The service interacting with DRBD the most is [Zynstra Sync](https://git.dev.zynstra.com/zynstra/startup-wiki/-/wikis/Superbad-Team-Wiki/Zynstra-Sync), as the service directly monitors the states of DRBD resources, and has the ability to invoke state changes on the resources themselves.

## Prepl

The DRBD interface specialised for resource replication, used to facilitate syncing between servers. The physical servers have a corresponding ethernet port with a cable connecting the two sides.

Bring it down or up with `ifconfig Prepl0 up/down`.

The Prepl `IP` is configured such that the final octet of the _"master"_ side is always `.1`, and the other `.2`. This means that the Prepl interface can be used to ssh between sides.

## Helpful Commands

- load the module - `modprobe drbd`
- sync drbd resources in parallel:
    - `drbdadm disk-options --resync-after -1 all`
    - after sync complete - `drbdadm adjust all`

## Resources

- [Docusaurus - DRBD & Zynstra](https://docs.dev.zynstra.com/docs/5.0/Startup/Infrastructure/DRBD)
- [LINBIT - DRBD Guide](https://linbit.com/drbd-user-guide/drbd-guide-9_0-en/)