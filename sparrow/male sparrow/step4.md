---
title: Hello World Container

---
4.

Docker has a builtin CLI. It comes by default with the Docker engine.

Let's understand how it works.

The first thing we can do is creating a Hello World container:

{{ execute }}
```
docker run --rm -it hello-world
```
{{ /execute }}

After using this command, Docker will, first of all, search for the image with the name "hello-world" locally, if it's not found, it will print this on the screen:

```
Unable to find image 'hello-world:latest' locally
```

This means that the image is not found on localhost, so Docker will start pulling it from the [Docker Hub](https://hub.docker.com/). This is why we see something like:

```yaml
latest: Pulling from library/hello-world
b8dfde127a29: Pull complete 
Digest: sha256:f2266cbfc127c960fd30e76b7c792dc23b588c0db76233517e1891a4e357d519
Status: Downloaded newer image for hello-world:latest
```

The Hello World container we ran will print a message then it will exit.