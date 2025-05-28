---
title: Volume creation
draft: false
tags:
---
 
```
docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/video/tv \
    tv

docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/video/movies \
    movies

docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/downloads \
    downloads

docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/roms \
    roms
    
docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/books \
    books
```