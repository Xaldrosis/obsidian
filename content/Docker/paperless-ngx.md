---
title: "paperless-ngx"
draft: false
tags:
---
```
services:
  broker:
    container_name: paperless-broker
    image: docker.io/library/redis:8
    restart: unless-stopped
    volumes:
      - redisdata:/data
    environment:
      - PUID=3000
      - PGID=3000
  db:
    container_name: paperless-db
    image: docker.io/library/postgres:17
    restart: unless-stopped
    volumes:
      - pgdata:/var/lib/postgresql/data
    environment:
      - POSTGRES_DB=paperless
      - POSTGRES_USER=paperless
      - POSTGRES_PASSWORD=paperless
      - PUID=3000
      - PGID=3000
  webserver:
    container_name: paperless-webserver
    image: ghcr.io/paperless-ngx/paperless-ngx:latest
    restart: unless-stopped
    depends_on:
      - db
      - broker
    ports:
      - "8010:8000"
    volumes:
      - data:/usr/src/paperless/data
      - paperless_media:/usr/src/paperless/media
      - ./export:/usr/src/paperless/export
      - paperless_consume:/usr/src/paperless/consume
    environment:
      - PAPERLESS_REDIS=redis://broker:6379
      - PAPERLESS_DBHOST=db
      - PUID=3000
      - PGID=3000
    env_file:
      - stack.env
volumes:
  data:
  paperless_media:
   external: true
  paperless_consume:
   external: true
  pgdata:
  redisdata:
```