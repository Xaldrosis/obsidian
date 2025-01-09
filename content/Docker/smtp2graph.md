---
title: smtp2graph
draft: false
tags:
---
 
```
volumes:
 smtp2graph:
services:
  smtp2graph:
    image: smtp2graph/smtp2graph:latest
    container_name: smtp2graph
    volumes:
      - smtp2graph:/config
    ports:
      - 587:587
    restart: unless-stopped
```