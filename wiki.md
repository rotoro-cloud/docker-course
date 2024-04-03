---
layout: page
title: Ansible infra
permalink: /wiki/
---


<style>
table.mytable
{
    border-collapse: collapse;
}

table.mytable td
{
    padding: 5px;
    border: 1px solid #AAA;
}

tr.head
{
    background: #EEE;
}
</style>


### Уровни архитектуры:

- Уровень балансировки (172.20.237.0).
  Используем популярные лоадбалансеры для разведения нагрузки.
- Уровень сервисов (172.20.236.0).
  Здесь находится бизнес-логика приложений и внутренние службы компании.
- Уровень данных (172.20.235.0).
  Здесь находятся базы данных нашей компании.

<table class="mytable">
    <tbody valign="middle">
        <tr class="head">
            <td>Назначение</td><td>Имя хоста</td><td>IP адрес</td><td>FQDN</td><td>User</td><td>Pass</td>
        </tr>
        <tr>
            <td>Джампхост для управления</td><td>controller</td><td>Динамический</td><td>controller.cloud.rotoro.corp</td><td>moon</td><td>selena</td>
        </tr>
        <tr>
            <td>Сервер базы данных</td><td>db01</td><td>172.20.235.10</td><td>db01.cloud.rotoro.corp</td><td>saturn</td><td>cronos</td>
        </tr>
        <tr>
            <td>Балансировщик нагрузки</td><td>lb01</td><td>172.20.237.10</td><td>lb01.cloud.rotoro.corp</td><td>mars</td><td>ares</td>
        </tr>
        <tr>
            <td>Сервер приложений №1</td><td>app01</td><td>172.20.236.101</td><td>app01.cloud.rotoro.corp</td><td>mercury</td><td>hermes</td>
        </tr>
        <tr>
            <td>Сервер приложений №2</td><td>app02</td><td>172.20.236.102</td><td>app02.cloud.rotoro.corp</td><td>venus</td><td>aphrodite</td>
        </tr>
        <tr>
            <td>Сервер приложений №3</td><td>app03</td><td>172.20.236.103</td><td>app03.cloud.rotoro.corp</td><td>earth</td><td>gaia</td>
        </tr>
        <tr>
            <td>Сервер хранения</td><td>str01</td><td>172.20.236.10</td><td>str01.cloud.rotoro.corp</td><td>jupiter</td><td>zeus</td>
        </tr>
        <tr>
            <td>Сервер резервного копирования</td><td>bu01</td><td>172.20.236.20</td><td>bu01.cloud.rotoro.corp</td><td>neptune</td><td>poseidon</td>
        </tr>
        <tr>
            <td>CI/CD сервер</td><td>cicd01</td><td>172.20.236.30</td><td>cicd01.cloud.rotoro.corp</td><td>uranus</td><td>celum</td>
        </tr>
        <tr>
            <td>Почтовый сервер</td><td>mail01</td><td>172.20.236.40</td><td>mail01.cloud.rotoro.corp</td><td>pluto</td><td>hades</td>
        </tr>
        <tr>
            <td>Сервер мониторинга</td><td>mon01</td><td>172.20.236.50</td><td>mon01.cloud.rotoro.corp</td><td>ceres</td><td>demeter</td>
        </tr>
    </tbody>
</table>


<img src="https://raw.githubusercontent.com/rotoro-cloud/rotoro-cloud.github.io/master/images/infrastructure.png">
