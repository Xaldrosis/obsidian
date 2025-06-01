---
title: swag
draft: false
tags:
---
 
```
volumes:
 swag:
services:
  swag:
    image: lscr.io/linuxserver/swag:latest
    container_name: swag
    cap_add:
      - NET_ADMIN
    environment:
      - TZ=Europe/Brussels
      - URL=xalnet.cc
      - VALIDATION=dns
      - SUBDOMAINS=unifi-network.home,portainer.home,sonarr.home,radarr.home,qbittorrent.home,bazarr.home,prowlarr.home,jellyfin.home,jellyseerr.home,pihole.home,tdarr.home,gamepanel.home,romm.home,readarr.home,calibre.home,calibre-web,netbox.home,paperless.home,huntarr.home
      - CERTPROVIDER=letsencrypt
      - DNSPLUGIN=cloudflare
      - EMAIL=tanzilsteven@hotmail.com
      - DOCKER_MODS=linuxserver/mods:swag-auto-reload
      - PROPAGATION=30
    volumes:
      - swag:/config
    ports:
      - 443:443
      - 80:80
    restart: unless-stopped
```