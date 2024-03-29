---
tags:
  - Personal
  - Programming
---
```yaml
version: "3"
services:
  calibre:
    image: lscr.io/linuxserver/calibre:latest
    container_name: calibre
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/London
      - PASSWORD= #optional
      - CLI_ARGS= #optional
    volumes:
      - /docker/calibre/config:/config
      - /mnt/mediadrive/Documents/Books:/books

    ports:
      - 32415:8080
      - 32184:8181
      - 41216:8081
    restart: unless-stopped
```