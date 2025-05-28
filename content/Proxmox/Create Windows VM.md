---
title: Create Windows VM
draft: false
tags:
---
 
## VM Configuration

![](proxmox_windows_1.png)![](proxmox_windows_2.png)
![](proxmox_windows_3.png)
![](proxmox_windows_4.png)

For Windows 11 leave the CPU type to the default value. Changing it to host will cause the VM to bluescreen.

![](proxmox_windows_5.png)![](proxmox_windows_6.png)
![](proxmox_windows_7.png)

## Windows Setup

I am leaving the language on English (United States) because I am planning to install Active Directory on it. I prefer to have my AD installed in English.

I am leaving the more obvious screenshots out.

![](proxmox_windows_8.png)
![](proxmox_windows_9.png)

You will notice the system does not find any hard drives. You will have to load the virtio iscsi drivers from the ISO mounted during VM creation.

![](proxmox_windows_10.png)
![](proxmox_windows_11.png)
![](proxmox_windows_12.png)
![](proxmox_windows_13.png)
![](proxmox_windows_14.png)

Once windows is installed open the virtio ISO and install the following 2 files.

![](proxmox_windows_15.png)