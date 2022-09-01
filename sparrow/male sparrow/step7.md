---
title: Running a container with a name

---
7.

Previously, we ran a container using `docker run -d brainarator/dummy` .

When this container starts running Docker gives it a random name.

You can check this using:

{{ execute }}
```
docker ps
```
{{ /execute }}

In order to give a container a name, we can use:

{{ execute }}
```
docker run -d --name dummy brainarator/dummy
```
{{ /execute }}

Executing the above command will create a new container using the same image but with a different name (dummy). You can check this using:

{{ execute }}
```
docker ps
```
{{ /execute }}