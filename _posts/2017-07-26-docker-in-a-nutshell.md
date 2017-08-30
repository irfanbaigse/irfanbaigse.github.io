---
layout: post
title: Docker in a Nutshell
image: /img/docker/docker-api.png
subtitle: Quick Introduction to Docker
show-avatar: true
comments: true
tags: [docker,docker-machine]
author: irfan
meta-data: images, containers, local daemons, volumes, networks, swarm nodes, swarm services
---


Docker is a platform or container technology.
Docker consists of a client and server. Client to issue commands and server to do the job and docker daemon listens and execute those commands. 

Docker Container Evolution

* Chroot by UNIX (Filesytem isolation)
* FreeBSD have jail utility
* Solaris offered containerization tech only limited to Solaris os
* Parallel inc -> Virtuozzo -> open sourced in 2005 
* Google CGroups
* Linux container in 2008
* Docker finally 2013 all pieces brought together to form containerization to mainstream

Surrounding Technologies

- Swarm
- Compose
- Machine
- Kitmatic
- Docker Trusted Registory
- Networking
- Service Delivery (To handle dynamic ip address of containers)
- Orchestration and cluster management (Kubernets , Mesos)

---

## Container Generation Process

---

![life-cycle](http://i.imgur.com/GK4mL2Y.png){:class="img-responsive"}

-----

### Dockerfile

---

```dockerfile
FROM ubuntu:15.04
ENV foo /bar
WORKDIR ${foo}   # WORKDIR /bar
ADD . $foo       # ADD . /bar
COPY \$foo /quux # COPY $foo /quux
```

Is a simple text file. Which contains simple below instructions

| FROM   | RUN 	      | ENV |
| COPY   | ENTRYPOINT | WORKDIR |
| EXPOSE | CMD        | VOLUME |


The `dockerfile` can be named anything. Best practice to name file ends with `filename.dockerfile`

Docker build images by reading `Dockerfile` instructions. `$ docker build` command is used to build image followed by the file path.
Docker daemon validates the docker file and returns error.

```commandline
$ docker build . #for current directory or 
$ docker build -f /path/to/dockerfile #you can specify the path
```

---

### Images

---
![docker-image](http://i.imgur.com/LEMZVVz.jpg){:class="img-responsive"}

Every instruction in `dockerfile` will create a layer of image. This layers act like cache, which increases reusability, decreases disk usage and help in speed up `docker build`. 

Images are not containers. Images are like blue prints like `class` in oop. Images are group of files that are built upon the core OS.
They are foundations to create and maintains official images.


```commandline
$ docker images # will list all the images 
```

---

### Container

---

![docker-image](http://i.imgur.com/i5ycI0Q.png?1){:class="img-responsive"}

Think of a Docker container as another way of virtualization. Virtual Machine(VM) allows sharing of hardware between different VMs to run on isolation.
Where as the containers share the OS, running isolated environments.

Containers are a way to package software to run in isolated environments. They are transportable pieces that can run anywhere
Linux is running

Conneting Containers to outside world

```commandline
$ docker run -d -p 8000:80 -t nginx
```
