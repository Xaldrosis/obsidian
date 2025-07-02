---
title: "Immich"
draft: false
tags:
---
```
services:
  immich-server:
    container_name: immich_server
    image: ghcr.io/immich-app/immich-server:release
    volumes:
      - immich_library:/usr/src/app/upload
      - /etc/localtime:/etc/localtime:ro
    ports:
      - '2283:2283'
    depends_on:
      - redis
      - database
    restart: always
    healthcheck:
      disable: false
  immich-machine-learning:
    container_name: immich_machine_learning
    image: ghcr.io/immich-app/immich-machine-learning:release
    volumes:
      - immich_model-cache:/cache
    restart: always
    healthcheck:
      disable: false
  redis:
    container_name: immich_redis
    image: docker.io/valkey/valkey:8-bookworm@sha256:fec42f399876eb6faf9e008570597741c87ff7662a54185593e74b09ce83d177
    healthcheck:
      test: redis-cli ping || exit 1
    restart: always
  database:
    container_name: immich_postgres
    image: ghcr.io/immich-app/postgres:14-vectorchord0.4.3-pgvectors0.2.0@sha256:5f6a838e4e44c8e0e019d0ebfe3ee8952b69afc2809b2c25f7b0119641978e91
    environment:
      POSTGRES_PASSWORD: ${DB_PASSWORD}
      POSTGRES_USER: postgres
      POSTGRES_DB: immich
      POSTGRES_INITDB_ARGS: '--data-checksums'
    volumes:
      - immich_postgress:/var/lib/postgresql/data
    restart: always
volumes:
  immich_model-cache:
  immich_postgress:
  immich_library:
   external: true
```