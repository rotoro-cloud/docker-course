---
layout: article
---
Ок, теперь еще один способ поиска образов, но теперь из CLI. Для этого мы используем команду `docker search httpd`.

```
docker search httpd
```

Поиск Docker отображает 25 строк результатов. Образов, связанных с httpd на Docker Hub очень много, давай сузим выборку. Добавим в команду опцию `--limit 2`.

```
docker search httpd --limit 2
```

Используя опцию лимита, мы ограничили результаты поиска только двумя образами. Максимально эта опция показывает 100 вхождений. Таким образом, если образов больше 100, поиск Docker частично ослепнет, имей это в виду. Придется как-то сузить свой запрос, чтобы данных возвращалось меньше.

Альтернативно мы можем использовать флаг `--filter` для фильтрации результатов найденных образов. Скажем, я хочу чтобы в выводе были образы, содержащие не менее 10 звезд.

```
docker search httpd --filter stars=10
```

Такой параметр, как звезды указывает на популярность образа. Как видишь, в выводе всего 3 образа, которые имеют как минимум
10 звезд. Есть еще один вариант фильтрации официальных образов. Для этого добавлю к команде флаг `--filter is-official=true`, как ты видишь. Мы можем объединить несколько разных фильтров в одну команду.

```
docker search httpd --filter stars=10 --filter is-official=true
```
