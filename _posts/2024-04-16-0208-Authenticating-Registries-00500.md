---
layout: article
---
Ок, как я сказал `image list` не всегда показывает настоящий размер занимаемого пространства. Для этих целей, т.е. для оценки занимаемого места, есть специальная команда `docker system df`. Она покажет нам реальный размер объектов, которыми занимается Docker. Это образы, контейнеры, тома и кэш сборщика.

```
docker image ls
```

```
docker system df
```

Как видишь, у меня всего 2 образа, хотя команда `image ls` выше утверждает, что их 4. Но как мы говорили, образы с одинаковым IMAGE ID - это один и тот же образ, который не занимает место дважды, что и подтверждает нижняя команда. Также `system df` показывает общий размер локальных образов и потенциальное количество места, занимаемое на диске, которое можно вернуть, удалив эти образы. Образ здесь рассматривается как `RECLAIMABLE`, если от него не создан ни один контейнер.

Количество образов, которые в данным момент задействованы в контейнерах, показывается в столбце `ACTIVE`. В моем примере оно в значении `0`, и это означает, что ни один образ хоста в данный момент не имеет порожденного от себя контейнера, поэтому мы можем рассчитывать на освобождение примерно 244 МБ после удаления ненужных образов. Сводкой из этой команды удобно воспользоваться перед тем, как начать чистить свой хост, когда на нем стало мало места.

Вот и все в этой лекции, увидимся в следующей!
