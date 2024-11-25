---
title: LXC Hardware Transcoding
draft: false
tags:
---
 
Open your shell on the Proxmox host.

```
nano /etc/subgid
```

Add the following text to the bottom. 104 is the render group.

```
root:104:1
```

Next open the configuration of your container.

```
nano /etc/pve/lxc/201.conf
```

Add the following to the bottom of the configuration. In case the render group has a different ID in the container, change the 104 to the correct ID and the 105 to the ID +1. The second 104 in "lxc.idmap: g 104 104 1" is the render group on the proxmox host.

```
lxc.cgroup2.devices.allow: c 226:0 rwm
lxc.cgroup2.devices.allow: c 226:128 rwm
lxc.mount.entry: /dev/dri/renderD128 dev/dri/renderD128 none bind,optional,create=file
lxc.idmap: u 0 100000 65536
lxc.idmap: g 0 100000 104
lxc.idmap: g 104 104 1
lxc.idmap: g 105 100106 65430
```

Add the root user to the render group.

```
usermod -aG render root
```