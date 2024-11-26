---
title: watchtower
draft: false
tags:
---
 
```
services:
  watchtower:
    container_name: watchtower
    hostname: watchtower
    image: containrrr/watchtower
    environment:
      - TZ=Europe/Brussels
      - WATCHTOWER_CLEANUP=true
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
```
