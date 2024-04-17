---
layout: article
---

Итак, по умолчанию контейнеры попадают в такую общую сетевую песочницу, где могут общаться с другими контейнерами, которые также создали без настроек. Мы можем создать свои собственные bridge-сети, в которых можем регулировать, какие именно контейнеры будут к ним подключены.

```
docker network create --subnet=172.15.0.0/24 first-net
```

```
docker network ls
```

```
docker container run -d --network first-net nicolaka/netshoot sleep 1d
```

Контейнер можно создать подключённым только к одной сети. Если попробовать сделать это сразу к нескольким, то мы получим ошибку.

```
docker network create second-net -d bridge
```

```
docker container create --net second-net --net first-net nicolaka/netshoot
```

Но мы можем подключить контейнер к нескольким сетям. Для этого для созданного контейнера нужно запустить команду `docker network connect`:

```
docker network connect second-net 2d3a
```

Если теперь заглянуть в контейнер, мы увидим в нём два сетевых интерфейса с разными адресами.

```
docker exec -it 2d3a ip a
```

```
docker network inspect second-net
```

Чтобы увидеть детали сети, используем команду `docker network inspect`. Как видишь, у `second-net` диапазон адресов `172.18.0.0/16`, и в эту сеть наш контейнер может посылать пакеты через интерфейс eth1.
