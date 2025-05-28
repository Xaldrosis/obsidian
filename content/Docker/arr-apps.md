---
title: arr-apps
draft: false
tags:
---
 
```
volumes:
 bazarr:
 movies:
  external: true
 tv:
  external: true
 radarr:
 downloads:
  external: true
 sonarr:
 jellyseerr:
services:
 bazarr:
  container_name: bazarr
  hostname: bazarr
  image: linuxserver/bazarr:latest
  ports:
    - 6767:6767
  volumes:
    - bazarr:/config
    - movies:/movies
    - tv:/tv
  environment:
    - PUID=3000
    - PGID=3000
    - TZ=Europe/Brussels
    - PATH=/lsiopy/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin 
  restart: unless-stopped
 radarr:
  container_name: radarr
  hostname: radarr
  image: linuxserver/radarr:latest
  ports:
    - 7878:7878
  volumes:
    - radarr:/config
    - downloads:/downloads
    - movies:/movies
  environment:
    - PUID=3000
    - PGID=3000
    - TZ=Europe/Brussels
  restart: unless-stopped
 sonarr:
  container_name: sonarr
  hostname: sonarr
  image: linuxserver/sonarr:latest
  ports:
    - 8989:8989
  volumes:
    - sonarr:/config
    - downloads:/downloads
    - tv:/tv
  environment:
    - PUID=3000
    - PGID=3000
    - TZ=Europe/Brussels
  restart: unless-stopped
 jellyseerr:
  container_name: jellyseerr
  hostname: jellyseerr
  image: fallenbagel/jellyseerr:latest
  ports:
    - 5055:5055
  volumes:
    - jellyseerr:/app/config
  environment:
    - TZ=Europe/Brussels
  restart: unless-stopped
```
