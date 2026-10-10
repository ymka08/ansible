# Домашнее задание к занятию 3 «Использование Ansible»

<img width="1840" height="324" alt="image" src="https://github.com/user-attachments/assets/fcfbd589-59c4-42f8-bec3-2aef0333201c" />


7-8
<img width="1612" height="824" alt="image" src="https://github.com/user-attachments/assets/d5353391-494f-45c4-a111-848d904b3c71" />
<img width="1646" height="656" alt="image" src="https://github.com/user-attachments/assets/054236ea-0417-47df-a7b6-f9c035c6ce94" />


Playbook состоит из трёх play.

На хостах группы clickhouse playbook:

- скачивает DEB-пакеты ClickHouse;
- устанавливает clickhouse-common-static;
- устанавливает clickhouse-client;
- устанавливает clickhouse-server;
- запускает или перезапускает сервис clickhouse-server;
- создаёт базу данных logs.

На хостах группы vector playbook:

- скачивает DEB-пакет Vector;
- устанавливает Vector;
- создаёт каталог /etc/vector;
- разворачивает конфигурацию Vector из шаблона templates/vector.yml.j2;
- перезапускает Vector при изменении конфигурации.

На хостах группы lighthouse playbook:

- устанавливает веб-сервер Nginx;
- скачивает архив со статическими файлами Lighthouse;
- распаковывает файлы в каталог /var/www/lighthouse;
- настраивает Nginx с помощью шаблона templates/lighthouse.conf.j2;
- создаёт символическую ссылку на конфигурацию сайта в /etc/nginx/sites-enabled;
- удаляет стандартную конфигурацию сайта Nginx;
- запускает Nginx и включает его в автозагрузку;
- перезапускает Nginx при изменении конфигурации.

Версия ClickHouse — 22.3.3.44.

Список пакетов ClickHouse: clickhouse-client, clickhouse-server, clickhouse-common-static.

Переменные ClickHouse находятся в group_vars/clickhouse/vars.yml.

Production inventory находится в inventory/prod.yml. В inventory определены три группы:

- clickhouse — сервер ClickHouse;
- vector — сервер Vector;
- lighthouse — сервер Lighthouse.

Шаблоны конфигурации находятся в каталоге templates: vector.yml.j2 для Vector и lighthouse.conf.j2 для Nginx.

