---
title: Docker Commands
draft: false
tags:
  - docker
---
## Start, stop, or restart a container

```
docker stop container_name
docker start container_name
docker restart container_name
```
## List docker-Container

List running containers:
```
docker ps -a
```

`-a` list all containers (running and stop)
## Delete docker-Container 

delete a stopped container:
```
docker rm container_name
```

`-f` to delete a running container

Delete all stopped containers:
```
docker container prune
```

## Show Docker-Logs
```
docker logs container_name
```
