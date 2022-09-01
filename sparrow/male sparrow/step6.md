---
title: Running a container in background

---
6.

When we ran the Hello World container it exited after executing a command.

The reason why this container exited is simply because it finishes what it was asked to do: print a hello world message.

In case you are running an application like a web app using Docker, your container should not and is not supposed to exit. This is why it should be executing a long-running command like a service (e.g.: Nginx, Apache, PHP, Node.js, ..etc).

Let's try running this container:

{{ execute }}
```
docker run -it brainarator/dummy
```
{{ /execute }}

The image we are using is an Alpine system executing this command `while true; do sleep 5 ; echo "container sleeping"; done`. This is why it will never exit.

You can stop it for now using they key combination:

```bash
CTRL + c
```

If you are running Mac, use:

```
Command + c
```

When we ran the previous container, it was attached to the terminal. It is possible to run the same container in detached mode, which means the container will run in background. To do this, we will use the `-d` flag:

{{ execute }}
```
docker run -d brainarator/dummy
```
{{ /execute }}

To check that the container is running in background, use:

{{ execute }}
```
docker ps
```
{{ /execute }}