# TASK

Запуск LAMP стека на Kubernetes
Требуется создать скрипт, который будет запускать контейнеризированный LAMP стек (Linux-Apache-MySQL-PHP) под управлением системы kubernetes. Внутри стека должно быть развернуто любое web-приложение на ваш выбор (например, взять CMS). Можно пользоваться готовыми  образами / контейнерами для отдельных компонентов.

Требования:
Приложение должно быть доступно из браузера на host системе.
Приложение должно взаимодействовать с базой данных - как минимум записывать некоторые данные.
Данные в БД не должны удаляться при потере контейнера с БД (использовать volumes).
При потере остальных контейнеров они должны перезапускаться автоматически.

## Prerequirements

You should use [helm](https://helm.sh/) 3 version

## Ingress

`Wordpress` helm chart contains Ingress resource. It's define `localhost:80/wp-admin` route to admin panel, `dev.localhost` route as site address. `PhpMyAdmin` ingress define `db.localhost` route for access.

## Template

You can view manifest of the chart using command below

```bash
helm template <chart_folder>
```

or

```bash
helm install <chart_name> <chart_folder> -o yaml --dry-run
```

## Deploy

```bash
helm install mysql charts/mysql
helm install phpmyadmin charts/phpMyAdmin
helm install wordpress charts/wordpress
```
