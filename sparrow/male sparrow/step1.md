---
title: How does Docker work?

---
1.

Docker has a client-server architecture. It uses a client and a daemon that can either run on the same host or on two different hosts (remote Docker daemon). 

These two components communicate using a REST API, over UNIX sockets or a network interface.

The client (docker) helps Docker users interact with containers, images, and other resources. 
When a user creates or build a container or an image, they use the Docker client (docker), and the client sends the commands to the daemon (dockerd).