---
title: Docker events

---
8.

When containers run they report events like: start, restart, kill and pause.

Let's understand how this works by running this container:

{{ execute }}
```
docker run -it \
--name dummy-events \
-d brainarator/dummy
```
{{ /execute }}

Let's execute a command like:

{{ execute }}
```
docker pause dummy-events
```
{{ /execute }}

Now, let's see what are the events that Docker reported:

{{ execute }}
```
docker events --since 2m
```
{{ /execute }}

By running the above command, you'll be able to see the events fired by the container during the last 2 minutes. If everything is alright, you will see two lines with both "start" and "pause" events.

```bash
[..] container start (image=brainarator/dummy, name=dummy-events)
[..] container pause (image=brainarator/dummy, name=dummy-events)
```

In reality the events you are seeing, are not just related to the container you created but to all containers running on the same machine.

You can filter by container using the `--filter` flag. 

Let's try it. First of all, unpause the container using 

{{ execute }}
```
docker unpause dummy-events
```
{{ /execute }}

Then execute:

{{ execute }}
```
docker events --since 10m --filter container=dummy-events
```
{{ /execute }}

Normally, you will be able to see the previous events related to our container (run, pause, unpause), unless you spent more than 10m executing the above commands. In this case, you can change 10m by another Go duration string like 50m or 1h30m or, use Unix timestamp instead.