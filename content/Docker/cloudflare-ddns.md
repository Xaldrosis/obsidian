---
title: "cloudflare-ddns"
draft: false
tags:
---
```
services:
  cloudflare-ddns:
    container_name: cloudflare-ddns
    hostname: cloudflare-ddns
    image: favonia/cloudflare-ddns:latest
    restart: always
    read_only: true
    cap_drop: [all]
    security_opt: [no-new-privileges:true]
    environment:
      - CLOUDFLARE_API_TOKEN=
      - DOMAINS=cobblemon.xalnet.cc,palworld.xalnet.cc,smtp.xalnet.cc,sophos.home.xalnet.cc,lab01.xalnet.cc,kasm.xalnet.cc
      - PROXIED=false 
```
