---
title: Getting information about Docker

---
3.

Docker is a very active project and its code is always changing. It is important to know which version you are running on your production and development servers.

`docker -v` will give you the version and the build number you are using.

{{ execute }}
```
docker -v
```
{{ /execute }}

You can also view other information about the server/client version, the architecture, the Go version ..etc. 

{{ execute }}
```
docker version
```
{{ /execute }}