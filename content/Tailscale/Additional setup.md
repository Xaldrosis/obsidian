---
title: Additional setup
draft: false
tags:
---
 
/dev/net/run passthrough

```
apt install sudo curl -y
```

```
echo 'net.ipv4.ip_forward = 1' | sudo tee -a /etc/sysctl.d/99-tailscale.conf
echo 'net.ipv6.conf.all.forwarding = 1' | sudo tee -a /etc/sysctl.d/99-tailscale.conf
sudo sysctl -p /etc/sysctl.d/99-tailscale.conf
```

```
sudo tailscale up --advertise-routes=172.19.90.0/24,172.19.92.0/24,172.19.93.0/24,192.168.5.0/24
```