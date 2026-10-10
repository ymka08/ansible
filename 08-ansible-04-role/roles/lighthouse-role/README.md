# Ansible Role: Lighthouse

Ansible-роль для развёртывания [Lighthouse](https://github.com/VKCOM/lighthouse) — веб-интерфейса для ClickHouse, работающего через Nginx.

## Requirements

- Ansible 2.19 или новее.
- Целевая ОС на базе Debian/Ubuntu с поддержкой `apt`.
- Доступ к интернету для установки Nginx и загрузки Lighthouse.

## Role Variables

Переменные по умолчанию определены в `defaults/main.yml`.

| Variable | Default | Description |
|---|---|---|
| `lighthouse_archive_url` | `https://github.com/VKCOM/lighthouse/archive/refs/heads/master.tar.gz` | URL архива Lighthouse |
| `lighthouse_document_root` | `/var/www/lighthouse` | Корневой каталог веб-приложения |
| `lighthouse_config_path` | `/etc/nginx/sites-available/lighthouse.conf` | Путь к конфигурации сайта Nginx |
| `lighthouse_port` | `80` | Порт HTTP-сервера |

## Example Playbook

---
- name: Install Lighthouse
  hosts: lighthouse
  become: true
  roles:
    - lighthouse-role
  tasks:
    - name: Check Lighthouse HTTP port
      ansible.builtin.wait_for:
        port: 80
        timeout: 30

## Configuration

Роль выполняет следующие действия:

1. Устанавливает Nginx.
2. Загружает и распаковывает архив Lighthouse.
3. Настраивает виртуальный хост Nginx.
4. Включает сайт и удаляет конфигурацию сайта по умолчанию.
5. Запускает Nginx и включает его автозапуск.

## Dependencies

Роль не требует отдельных Ansible-ролей: установка и настройка Nginx выполняются непосредственно внутри неё.

## License

MIT
