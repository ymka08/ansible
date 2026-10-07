# Домашнее задание к занятию 2 «Работа с Playbook»

5-8

<img width="1709" height="890" alt="image" src="https://github.com/user-attachments/assets/da849d71-e77a-45e8-8faa-9396c79276f7" />


<img width="1207" height="147" alt="image" src="https://github.com/user-attachments/assets/f7c3e6be-18e2-467f-a0d4-09eeed563e31" />


<img width="1698" height="871" alt="image" src="https://github.com/user-attachments/assets/4443a9d7-8cde-43be-aedd-d9da0eeb6d7c" />
<img width="1692" height="710" alt="image" src="https://github.com/user-attachments/assets/8edd49f5-8a36-4dfd-bea8-d40cec8451c4" />

<img width="1685" height="822" alt="image" src="https://github.com/user-attachments/assets/2e1187c1-f5c7-4001-9daf-0b05f5f320e8" />


Playbook состоит из двух play.

На хостах группы clickhouse playbook:
- скачивает DEB-пакеты ClickHouse
- устанавливает clickhouse-common-static
- устанавливает clickhouse-client
- устанавливает clickhouse-server
- запускает или перезапускает сервис clickhouse-server
- создаёт базу данных logs.

На хостах группы vector playbook:
- скачивает DEB-пакет Vector
- устанавливает Vector
- создаёт каталог /etc/vector
- разворачивает конфигурацию Vector из шаблона templates/vector.yml.j2
- перезапускает Vector при изменении конфигурации.

Версия ClickHouse 22.3.3.44
Список пакетов ClickHouse clickhouse-client, clickhouse-server, clickhouse-common-static
Переменные ClickHouse находятся в group_vars/clickhouse/vars.yml

Production inventory находится в inventory/prod.yml
В inventory определены две группы:
clickhouse — сервер ClickHouse
vector — сервер Vector
