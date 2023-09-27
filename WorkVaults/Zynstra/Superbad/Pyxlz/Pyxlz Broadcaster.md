---
alias: Broadcaster
---
# Sharing information across clusters - 

## Overview of Feature

As part of the [[Pyxlz]] package we have `broadcaster` - a part of `pyxlz` running in the background, sharing the information across with the remote zhapcon. This feature was initially created to keep the other side informed about `pyxlz` related information (eg. `remote_run`/`remote_ready` states of VMs), but has since grown to include stuff like sharing cluster versions and storing it in Xenstore.

[[Pyxlz Broadcaster|Broadcaster]] is part of `pyxlz` and is instantiated as part of `pyxlzd` object of `pyxlz/daemon`. It consists of a `broadcaster` and an `aerial` component. `Broadcaster` sends the local information across, whereas `aerial` receives information from all other zhapcons (and processes / stores it, as necessary).

Pre **4.12** version the broadcaster was broadcasting only across `Prepl0` and `xenet` interfaces of `zhapcon`, with non-encrypted traffic. Since **4.12** we are now also using LAN/WAN to broadcast so the traffic is now encrypted using Python's `cryptography.fernet` mechanism.

As of **4.12** the following is broadcasted via broadcaster:

- `dom0-admin-state` - enables eg. `zstop` and `zstart` action to apply on both sides simultaneously when ran from CLI only on one side
- various `remote-ready-d` keys, `remote-run` entry and `remote-data` (related to VNC ports)
- `version` information - see **Version Sharing** section below

### Version Sharing

One of the features `broadcaster` fulfills these days, other than internal `pyxlz` stuff, is the **version sharing**.

The versions are read locally from `/zynstra/config/binary-patch/config/hap.version` and are shared with the other side periodically. Every side keeps track of 3 values - `local_version`, `remote_version` and `lowest_version`. The first two are read/received, the `lowest_version` is computed.

All of them are stored as `strings` in `xenstore` under `/tools/zynstra/global/{local,lowest,remote}_version`:

```
>>> xenstore-ls /tools/zynstra/global | grep versionlocal_version = "9000000"remote_version = "9000000"lowest_version = "9000000"
```

Their main usefulness is in **enabling backwards compatibility sensitive code** to turn various features on/off based on, for example, the lowest version across all sides. This is a common thing to resolve for us and so far, these checks are our best way to deal with it.

## Configuration

There is no configuration specific to the `broadcaster`. It will use all interfaces available to it and since it uses broadcasting, it doesn't really target specific addresses.

## Debug

Since `broadcaster` is part of `pyxlz`, for debugging you'd want to look at `journalctl -u zynstra-pyxlzd`. The logging is silent by default, so turning the level to `DEBUG` for `pyxlz` and restarting the service is recommended if debugging this.

If you feel like the information that is supposed to be shared isn't, **the first thing to look at should be the interfaces and their health**. If all of that looks ok, it might be that the encryption/decryption is not working. Please contact engineering for further help at this point.