---
title: SDN
draft: false
tags:
---
 
The SDN feature allows us to create zones and networks. This will simplify the advanced network configuration in Proxmox.

Create a zone for each of your bridges.

![](proxmox_sdn_1.png)

Give the zone a name and type the correct bridge name.

![](proxmox_sdn_2.png)

Now go to VNets and click on "Create".

![](proxmox_sdn_3.png)

Now select the name for the VNet, the zone and add the correct vlan tag.

![](proxmox_sdn_4.png)

To save your settings go back to SDN and click on "Apply".

![](proxmox_sdn_5.png)

Once this is saved you can go back to your VM Network Device and select the newly created VNet. Make sure to remove the VLAN Tag as well. As you can see this simplifies configuring VLANs on your VMs.

![](proxmox_sdn_6.png)
