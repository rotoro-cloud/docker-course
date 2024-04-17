---
layout: article
---

Для получения списка мы используем команду `docker network ls`. Как ты помнишь, изначально существуют три `pre-defined networks`:

```
docker network ls
```

Чтобы запустить контейнер, который должен быть подключен к определённой сети, нужно указать ее название или ID в параметре `--network` или короче `--net` при создании контейнера.

Если этого не задать, то контейнер подключится к сети `bridge`. Эта сеть существует всегда, и мы не можем её удалить, только задать некоторые параметры через настройки Docker.

```
{
    "hosts": ["unix:///var/run/docker.sock", "tcp://0.0.0.0:2375"],
    "exec-opts": [
      "native.cgroupdriver=cgroupfs"
    ],
    "bip":"172.12.0.1/24",
    "registry-mirrors": [
      "http://docker-registry-mirror.rotoro.cloud"
    ]
}
```

Вот пример файла конфигурации моих лабораторных. Мы можем проверить, что эта сеть имеет кастомную адресацию при помощи `network inspect`:

```
docker network inspect bridge | grep -i subnet
```
