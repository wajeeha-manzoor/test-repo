---
title: Docker and filesystem

---
A Docker container is ephemeral. It means it can be created, stopped and destroyed then replaced with the same image to run again. 

This characteristic enables Docker to be a good fit for cloud native projects. However, from a storage point of view, an ephemeral container means that a destroyed container has its filesystem destroyed too.

If you are running a simple application that doesn't use storage inside a container, that's not a problem. However, once you start building applications that use databases, the ephemeral storage of containers is not a good fit. 

You will lose all the data in your database once the container is destroyed.

This is when volumes are helpful. Running a database container is a good use case.