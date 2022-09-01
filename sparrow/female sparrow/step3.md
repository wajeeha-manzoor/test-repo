---
title: Bind mounts

---
Previously we ran a database container using `docker run --name mariadb -e MYSQL_ROOT_PASSWORD=p455w0rd -d mariadb`. We understood how container storage by default will not preserve your data. 
However, there is something we can do to preserve data, even when the container is destroyed which is Docker bind mounts.

{{ execute }}
```
docker run \
--name mariadb-bind-mount \
-e MYSQL_ROOT_PASSWORD=p455w0rd \
-v /data/db:/var/lib/mysql \
-d mariadb
```
{{ /execute }}

If you go to `/data/db`, you will find how Docker mounted the `/var/lib/mysql` from inside the container to the host:

{{ execute }}
```
ls -l /data/db/
```
{{ /execute }}

Remove the container:

{{ execute }}
```
docker rm -f mariadb-bind-mount
```
{{ /execute }}

Now check the mounted folder:

{{ execute }}
```
ls /data/db
```
{{ /execute }}

The database files were preserved.