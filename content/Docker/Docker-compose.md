---
title: Docker-compose
draft: false
tags:
  - docker
  - docker-compose
---
# Boilderplate

`Docker-compose.yml`:

```yml
services:
  app:
    image: supersoftware/app:latest # image, which will pull the :latest version of the application
    restart: unless-stopped # The container will always restart unless it is explicitly stopped
    container_name: "supersoftware-app" # app name in network
    ports: # Maps port 80 on the host to port 80 on the container, making the application accessible via the host's port 80
    # <Host Port>:<Container Port>
      - "80:80"
    networks:
      - "lan" # An external network allowing access to other containers in the same network
      - "pan" # A dedicated network specific to this setup
    volumes:
      - ./data:/data # "./" creates the directory inside this folder
      - /etc/localtime:/etc/localtime:ro

  db:
    image: supersoftware/db:latest
    restart: unless-stopped
    container_name: "supersoftware-db"
    networks:
      - "pan"
    volumes:
      - ./var_lib_spdb:/var/lib/spdb
      - /etc/localtime:/etc/localtime:ro #make sure only read-only
    enviroment:
      SPDB_HOSTNAME: spdb # simple names or config is ok in docker-compose.yml file
      SPDB_URL: http://superdb.local/db/ # simple config ok in docker-compose.yml file
      SPDB_USER: ${SPDB_USER} # everything with credentials in .env file
      SPDB_PWD: ${SPDB_PWD} # look .env file

networks:
  lan:
    external: true # when access to other containers
  pan: # for dedicated network in container better than app_default
```

## Update Container

```shell
git pull
docker compose pull
docker compose up -d
```
## Start Container

```shell
docker compose up -d
```

`-d` run as deamon (in background)