---
title: Inspecting Volumes

---
In order to find out which volume a container is using, we can use the `docker inspect` command.

Let's use it with the container "mariadb-with-volume":

{{ execute }}
```
docker inspect mariadb-with-volume
```
{{ /execute }}

Even if this command will show the configuration of the container including its volumes and their respective paths (`/var/lib/docker/volumes/<volume_id>`), it is hard to find out in the printed JSON.

We can use the following command instead:

{{ execute }}
```
docker inspect -f '{{ (index .Mounts 0).Destination }}' mariadb
```
{{ /execute }}

In order to get the "Source" of the volume, use:

{{ execute }}
```
docker inspect -f '{{ (index .Mounts 0).Source }}' mariadb-with-volume
```
{{ /execute }}