---
title: "Upgrade to Trixie"
draft: false
tags:
---
 
```
sed -i 's/bookworm/trixie/g' /etc/apt/sources.list
apt update && apt dist-upgrade -y
reboot
```