---
title: Docker Commands
draft: false
tags:
  - docker
  - linux
author: stormy
---
## Start, stop, or restart a Container

```bash
docker stop mein_container_name 
docker start mein_container_name 
docker restart mein_container_name 
```
## Delete a Container

To delete a stopped container, use:
```bash
docker rm container_id_or_name
```

To delete a running container, use:
```bash
docker rm -f container_id_or_name
```

To delete all stopped containers you can use:
```bash
docker container prune
```
## Show Container

```bash
docker ps -a
```

`-a` alle Container (laufende und gestoppte) anzeigen
## Show Docker-Logs

```bash
docker logs container_id_or_name
```
## Accessing a Docker container

```bash
docker exec -it container_id_or_name
```
## Monitor Container Memory and CPU Usage

```bash
docker stats
```