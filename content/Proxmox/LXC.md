---
title: LXC
draft: false
tags:
---
 
### Downloading LXC Template

Go to your storage which has "CT Templates" enabled and click on "Templates".

![](proxmox_lxc_1.png)

Select the distribution you want to use for your LXC and click on "Download".

![](proxmox_lxc_2.png)

### Create LXC

Click "Create CT" in the top right corner.

![](proxmox_lxc_3.png)

Give your container a hostname and password. Click on "Next".

![](proxmox_lxc_4.png)

Select the storage and template you wish to use. Click on "Next".

![](proxmox_lxc_5.png)

Choose where you want to save the LXC disk and click on "Next".

![](proxmox_lxc_6.png)

Choose how much CPU power this container may use. Click on "Next".

![](proxmox_lxc_7.png)

Set how much memory the container may use.

![](proxmox_lxc_8.png)

Select the correct network interface and assign an IP address if needed. Click on "Next".

![](proxmox_lxc_9.png)

Set the DNS settings and click on "Next".

![](proxmox_lxc_10.png)

After reviewing the settings you may click on "Finish". In case you want the container to instantly start, select "Start after created".

![](proxmox_lxc_11.png)

The container will now be created from the template. Once the container has started, you can login with the user "root" and the password you have set during the install.