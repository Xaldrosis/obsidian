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
    --opt device=:/mnt/data/proxmox/docker/portainer \
    portainer

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
    --opt device=:/mnt/data/proxmox/docker/bazarr \
    bazarr

docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/docker/radarr \
    radarr

docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/docker/sonarr \
    sonarr

docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/docker/jellyseerr \
    jellyseerr

docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/docker/unifi \
    unifi

docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/docker/unifidb \
    unifidb

docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/docker/gluetun \
    gluetun

docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/docker/qbittorrent \
    qbittorrent

docker volume create \
    --driver local \
    --opt type=nfs \
    --opt o=addr=172.19.90.3,rw,nfsvers=4 \
    --opt device=:/mnt/data/proxmox/docker/prowlarr \
    prowlarr
```