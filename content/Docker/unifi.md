---
title: unifi
draft: false
tags:
---
 
```
volumes:
 unifidb:
 unifidbconfig:
 unifi:
services:
 unifi-db:
  image: mongo:4
  container_name: unifi-db
  volumes:
    - unifidb:/data/db
    - unifidbconfig:/data/configdb
  environment:
    - TZ=Europe/Brussels
  restart: unless-stopped
 unifi-network-application:
  image: linuxserver/unifi-network-application:latest
  container_name: unifi-network-application
  environment:
    - TZ=Europe/Brussels
    - MONGO_USER=unifi
    - MONGO_PASS=
    - MONGO_HOST=unifi-db
    - MONGO_PORT=27017
    - MONGO_DBNAME=unifi
  volumes:
    - unifi:/config
  ports:
    - 8443:8443
    - 3478:3478/udp
    - 10001:10001/udp
    - 8080:8080
  restart: unless-stopped
```
