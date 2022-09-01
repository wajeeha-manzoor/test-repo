---
title: Docker volumes

---
In the previous step, we mapped the Docker container folder to a folder on our localhost. This means any process or user can access MariaDB files. Also, there is nothing that really link between the container and its data. Other containers may use the same folder by mistake and may change it.

Docker volumes are the preferred way to keep data.

{{ execute }}
```
docker run \
--name mariadb-with-volume \
-e MYSQL_ROOT_PASSWORD=password \
-v /var/lib/mysql \
-d mariadb
```
{{ /execute }}

You can check all existing volumes using:

{{ execute }}
```
docker volume ls
```
{{ /execute }}

Docker volumes are stored under `/var/lib/docker/volumes`.