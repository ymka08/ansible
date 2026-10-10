# Домашнее задание к занятию 4 «Работа с roles»

## Описание

Playbook автоматизирует установку и настройку ClickHouse, Vector и Lighthouse с использованием Ansible-ролей.

## Используемые роли

- **ClickHouse** — установка и настройка ClickHouse.
- **Vector** — установка и настройка Vector для обработки логов.
- **Lighthouse** — установка веб-интерфейса Lighthouse для ClickHouse.

## Переменные и настройки

- inventory/prod.yml — состав серверов и групп хостов.
- group_vars/clickhouse/vars.yml — переменные для ClickHouse.
- requirements.yml — список ролей и источники их загрузки.
- ansible.cfg — настройки Ansible.
- site.yml — основной playbook, запускающий установку ролей.

## Запуск

Установить необходимые роли:

ansible-galaxy install -r requirements.yml -p ../roles

Синтаксис playbook:

ansible-playbook -i inventory/prod.yml site.yml --syntax-check

Список задач:

ansible-playbook -i inventory/prod.yml site.yml --list-tasks

Запустить playbook:

ansible-playbook -i inventory/prod.yml site.yml


## Используемые репозитории ролей

- [Vector role](https://github.com/ymka08/vector-role)
- [Lighthouse role](https://github.com/ymka08/lighthouse-role)


---
