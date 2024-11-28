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
      - URL=home.xalnet.cc
      - VALIDATION=dns
      - SUBDOMAINS=wildcard
      - CERTPROVIDER=letsencrypt
      - DNSPLUGIN=cloudflare
      - EMAIL=
      - DOCKER_MODS=linuxserver/mods:swag-auto-reload
    volumes:
      - swag:/config
    ports:
      - 443:443
      - 80:80
    restart: unless-stopped
```