---
layout: article
---
Ранее мы запускали контейнеры при помощи команды `docker container run`. В процессе работы, Docker проверял, присутствует ли образ на локальном хосте, и если он не мог его найти, то забирал его из репозитория образов. После этого он запускал контейнер.

Если мы просто хотим загрузить образ и оставить его, чтобы запустить позже, то для этого в Docker есть специальная команда `image pull`, и мы ей недавно пользовались. 

```
docker image pull httpd
```

Вот здесь я запустил команду `docker image pull httpd`. Это загрузит образ, распакует его и сохранит на диск docker-хоста. Теперь контейнер будет создан гораздо быстрее, поскольку не будет затрачиваться время на скачивание образа из сети и его распаковку.

Просмотреть локальные образы мы можем при помощи `docker image ls`:

```
docker image ls --no-trunc
```

Это похоже, как мы получали листинг контейнеров при помощи `container ls`. Аналогично с ними можно использовать опции `-q` и `--no-trunc`.
