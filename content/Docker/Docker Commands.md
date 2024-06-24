---
title: Docker Commands
draft: false
tags:
  - docker
---
## Docker Commands
### Start, stop, or restart a container.

```
docker stop mein_container_name 
docker start mein_container_name 
docker restart mein_container_name 
```
### Docker-Container löschen

Um einen gestoppten Container zu löschen, benutze:
```
docker rm container_id_or_name
```

Um alle gestoppten Container zu löschen, kannst du folgendes benutzen:
```
docker container prune
```
### Docker-Container anzeigen

Um eine Liste aller laufenden Container anzuzeigen, benutze:
```
docker ps -a
```

`-a` alle Container (laufende und gestoppte) anzeigen
### Docker-Logs anzeigen

Um die Logs eines Containers anzuzeigen, benutze:
```
docker logs container_id_or_name
```
### Docker-Container löschen (auch wenn er läuft)

Um einen laufenden Container zu löschen (dies stoppt ihn zuerst), benutze:
```
docker rm -f container_id_or_name
```

Das sind die grundlegenden Befehle, die dir den Einstieg in Docker erleichtern sollten. Wenn du weitere spezifische Fragen oder Anwendungsfälle hast, lass es mich wissen!