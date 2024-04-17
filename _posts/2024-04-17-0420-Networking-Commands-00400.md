---
layout: article
---

Отключить контейнер от сети можно без остановки при помощи команды `network disconnect`. При этом внутри контейнера пропадёт сетевой интерфейс.

```
docker network disconnect second-net 2d3a
```

```
docker exec -it 2d3a ip a
```
