---
title: vpn-protected
draft: false
tags:
---
 
```
volumes:
 gluetun:
  external: true
 qbittorrent:
  external: true
 prowlarr:
  external: true
 downloads:
  external: true
services:
  gluetun:
    image: qmcgaw/gluetun:latest
    container_name: gluetun
    cap_add:
      - NET_ADMIN
    devices:
      - /dev/net/tun:/dev/net/tun
    volumes:
      - gluetun:/gluetun:nocopy
    environment:
      - PUID=3000
      - PGID=3000
      - TZ=Europe/Brussels
      - LOG_LEVEL=debug
      - VPN_SERVICE_PROVIDER=custom
      - VPN_TYPE=openvpn
      - FIREWALL_DEBUG=off
      - VPN_INTERFACE=tun0
      - OPENVPN_CUSTOM_CONFIG=/gluetun/custom.conf
      - FIREWALL_OUTBOUND_SUBNETS=172.19.91.0/24,172.19.93.0/24
    ports:
      - 8888:8888/tcp
      - 8388:8388/tcp
      - 8388:8388/udp
      - 8089:8089
      - 8191:8191
      - 9696:9696
    restart: unless-stopped
  qbittorrent:
    image: linuxserver/qbittorrent
    container_name: qbittorrent
    environment:
      - PUID=3000
      - PGID=3000
      - TZ=Europe/Brussels
      - WEBUI_PORT=8089
    volumes:
      - qbittorrent:/config:nocopy
      - downloads:/downloads:nocopy
    network_mode: "service:gluetun"
    restart: unless-stopped
  flaresolverr:
    image: flaresolverr/flaresolverr:latest
    container_name: flaresolverr
    environment:
      - LOG_LEVEL=info
    network_mode: "service:gluetun"
    restart: unless-stopped
  prowlarr:
    image: linuxserver/prowlarr:latest
    container_name: prowlarr
    environment:
      - PUID=3000
      - PGID=3000
      - TZ=Europe/Brussels
    volumes:
      - prowlarr:/config:nocopy
    network_mode: "service:gluetun"
    restart: unless-stopped
```