---
title: Using Docker help

---
2.

You can view the Docker help using the command line:

{{ execute }}
```
docker --help
```
{{ /execute }}

You will get a list of options like `-v`, management commands like `network` and other commands like `cp` and `exec`.

If you need more help with a specific command like `cp` or `rmi` , you need to type:

{{ execute }}
```
docker cp --help
docker rmi --help
```
{{ /execute }}

In some cases, you can have three levels of help like:

{{ execute }}
```
docker swarm init --help
```
{{ /execute }}