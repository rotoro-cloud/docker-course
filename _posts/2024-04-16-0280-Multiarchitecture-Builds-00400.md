---
layout: article
---

BuldKit умеет собирать образы под различные архитектуры, скрывая от нас всю сложность. Если целевая архитектура отличается от хостовой, он использует QEMU-виртуализацию. Но это не работает с дефолтным драйвером сборки. Т.е. нам нужно использовать драйвер, отличный от `docker`. В моём примере это будет `docker-container`.

```
DOCKER_BUILDKIT=1 docker buildx create --name builder --driver docker-container --use
```

Сначала я создал билдер, который может использовать сборочный контейнер при создании образов, и далее проинструктировал использовать его по-умолчанию.

```
docker buildx inspect --bootstrap
```

Как видишь, мне доступны только `linux/amd64, linux/amd64/v2, linux/386`. Это потому, что я не настроил виртуализацию на хосте. Чтобы не делать это вручную, я могу использовать контейнер, который мне все настроит:

```
docker container run --rm --privileged multiarch/qemu-user-static --reset -p yes
```

Теперь, после того, как quemu настроен, я могу собирать для остальных архитектур.

```
docker buildx inspect --bootstrap
```

Как видишь, у меня добавились новые варианты.
Для поверки я буду использовать тестовое go-приложение от `GCP`.

```
git clone https://github.com/GoogleCloudPlatform/golang-samples.git
```

```
cd golang-samples/run/helloworld/
```

Это простое приложение с двумя стадиями сборки, которое поднимает веб-сервер на порту 8080 и возвращает `Hello World!`. Я упущу лишние детали в Dockerfile.

```
cat Dockerfile
...
FROM golang:1.21-bookworm as builder
....
FROM debian:bookworm-slim
...
CMD ["/app/server"]
```

Теперь соберу образ и запущу его. У меня процесс занял меньше минуты. Ключ `--load` говорит экспортеру загрузить готовый образ в локальное хранилище docker-хоста.

```
DOCKER_BUILDKIT=1 docker buildx build --tag helloworld:v1 --load .
```

Далее я запускаю контейнер с маппингом хостового порта `8080` и проверяю, отвечает ли приложение.

```
docker container run -p 8080:8080 -d helloworld:v1
```

```
curl localhost:8080
```
