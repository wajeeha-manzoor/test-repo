---
title: Docker run flags

---
5.

We executed Docker run to run Hello World, and we used:

{{ execute }}
```
docker run --rm -it hello-world
```
{{ /execute }}

Let's understand what `--rm` and `-it` mean.

`--rm` flag ask Docker to clean up. This means that Docker will clean up the container and remove the file system when the container exits.

On the other hand, the `-it`  allocates a tty for the container process. This flag is used to run Docker containers in interactive modes. The tty connects the Docker terminal with the stdin and stdout stream of our local machine, this allows us to run commands and read the output on/from the container. In other words, you can execute commands (using bash/shell) inside the container **while it is still running**.

We could have used `-i -t` instead of `-it`.

There are other flags and options we can use when we run Docker containers. We are going to discover them.