---
title: unifi
draft: false
tags:
---
 
```
volumes:
 unifidb:
  external: true
 unifi:
  external: true
services:
 unifi-db:
  image: mongo:4
  container_name: unifi-db
  user: "3000"
  volumes:
    - unifidb:/data/db:nocopy
  environment:
    - TZ=Europe/Brussels
  restart: unless-stopped
 unifi-network-application:
  image: linuxserver/unifi-network-application:latest
  container_name: unifi-network-application
  environment:
    - PUID=3000
    - PGID=3000
    - TZ=Europe/Brussels
    - MONGO_USER=unifi
    - MONGO_PASS=
    - MONGO_HOST=unifi-db
    - MONGO_PORT=27017
    - MONGO_DBNAME=unifi
  volumes:
    - unifi:/config:nocopy
  ports:
    - 8443:8443
    - 3478:3478/udp
    - 10001:10001/udp
    - 8080:8080
  restart: unless-stopped
```
