---
layout: article
---
```
journalctl -u docker
```

Чтобы получить информацию из логов воспользуемся командой `journalctl -u docker.service`. Это должно дать нам дополнительную информацию о проблеме.

Что касается Windows, то логи демона расположены в папке `~AppData\Local\Docker`, и их можно просмотреть через `Windows Event Viewer`.
