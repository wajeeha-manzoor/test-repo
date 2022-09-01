---
title: Dangling Volumes

---
Dangling volumes are Docker volumes not referenced by any container. When developing using Docker, you can quickly accumulate multiple unused volumes that consumes disk space.

Let's create a volume for the sake of example:

{{ execute }}
```
docker volume create my-volume-1
docker volume create my-volume-2
```
{{ /execute }}

Check if it's in the volumes list:

{{ execute }}
```
docker volume ls
```
{{ /execute }}

"my-volume-1" and "my-volume-2" are dangling volumes since they are not attached to any container. We can check that by listing all dangling volumes:

{{ execute }}
```
docker volume ls -f dangling=true
```
{{ /execute }}

In order to remove all dangling volumes, use the following command:

{{ execute }}
```
docker volume rm $(docker volume ls -f dangling=true -q)
```
{{ /execute }}

Or simply use the `docker volume prune` command:

{{ execute }}
```
docker volume prune
```
{{ /execute }}