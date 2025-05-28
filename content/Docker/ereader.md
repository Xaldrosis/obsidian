---
title: "ereader"
draft: false
tags:
---
```
volumes:
 readarr:
 books:
  external: true
 downloads:
  external: true
 calibre:
 calibre-web:
services:
 readarr:
  container_name: readarr
  hostname: readarr
  image: linuxserver/readarr:develop
  ports:
    - 8787:8787
  volumes:
    - readarr:/config
    - books:/books
    - downloads:/downloads
  environment:
    - PUID=3000
    - PGID=3000
    - TZ=Europe/Brussels
  restart: unless-stopped
 calibre:
  container_name: calibre
  hostname: calibre
  image: linuxserver/calibre:latest
  ports:
    - 8280:8080
    - 8181:8181
    - 8081:8081
  volumes:
    - calibre:/config
    - books:/books
  environment:
    - PUID=3000
    - PGID=3000
    - TZ=Europe/Brussels
  restart: unless-stopped
 calibre-web:
  container_name: calibre-web
  hostname: calibre-web
  image: linuxserver/calibre-web:latest
  ports:
    - 8083:8083
  volumes:
    - calibre-web:/config
    - books:/books
  environment:
    - PUID=3000
    - PGID=3000
    - TZ=Europe/Brussels
  restart: unless-stopped
```
