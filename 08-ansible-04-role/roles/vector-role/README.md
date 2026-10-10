# Ansible Role: Vector

Ansible-роль для установки и настройки [Vector](https://vector.dev/) — инструмента для сбора и обработки логов.

## Requirements

- Ansible 2.19 или новее.
- Целевая ОС на базе Debian/Ubuntu с поддержкой `apt`.
- Доступ к интернету для загрузки пакета Vector.

## Role Variables

Переменные по умолчанию определены в `defaults/main.yml`.

| Variable | Default | Description |
|---|---|---|
| `vector_data_dir` | `/var/lib/vector` | Каталог данных Vector |
| `vector_log_paths` | `[/var/log/*.log]` | Список путей к файлам логов |
| `vector_config_path` | `/etc/vector/vector.yml` | Путь к конфигурационному файлу |
| `vector_package_url` | `https://packages.timber.io/vector/0.33.0/vector_0.33.0-1_amd64.deb` | URL пакета Vector |
| `vector_package_path` | `/tmp/vector.deb` | Путь для скачанного пакета |

## Example Playbook

---
- name: Install Vector
  hosts: vector
  become: true
  roles:
    - vector-role

## Configuration

Роль скачивает и устанавливает Vector, создаёт каталог конфигурации и формирует файл конфигурации из шаблона `templates/vector.yml.j2`.


## License

MIT
