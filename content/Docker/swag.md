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
      - SUBDOMAINS=wildcard
      - EXTRA_DOMAINS=*.home.xalnet.cc
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