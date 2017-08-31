---
layout: post
title: Docker in 5 Minutes
image: /img/docker/docker.png
subtitle: Quick Introduction to Docker
show-avatar: true
comments: true
tags: [docker,docker-machine,docker images, docker containers]
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
|----    | ---- |   ---- |
| __COPY__   | __ENTRYPOINT__ | __WORKDIR__ |
| __EXPOSE__ | __CMD__        | __VOLUME__ |


The `dockerfile` can be named anything. Best practice to name file ends with `filename.dockerfile`

Docker build images by reading `Dockerfile` instructions. `$ docker build` command is used to build image followed by the file path.
Docker daemon validates the docker file and returns error.

```commandline
$ docker build . #for current directory or 
$ docker build -f /path/to/dockerfile #you can specify the path
```

---

### Docker Image

---
![docker-image](http://i.imgur.com/LEMZVVz.jpg){:class="img-responsive"}

Every instruction in `dockerfile` will create a layer of image. This layers act like cache, which increases reusability, decreases disk usage and help in speed up `docker build`. 

Images are not containers. Images are like blue prints like `class` in oop. Images are group of files that are built upon the core OS.
They are foundations to create and maintains official images.

Docker images commands

* `docker image build`	Build an image from a Dockerfile
* `docker image import`	Import the contents from a tarball to create a filesystem image
* `docker image inspect`	Display detailed information on one or more images
* `docker image load`	Load an image from a tar archive or STDIN
* `docker image ls`	List images
* `docker image prune`	Remove unused images
* `docker image pull`	Pull an image or a repository from a registry
* `docker image push`	Push an image or a repository to a registry
* `docker image rm`	Remove one or more images
* `docker image save`	Save one or more images to a tar archive (streamed to STDOUT by default)
* `docker image tag`	Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

---

### Docker Container

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
Docker container commands

* `docker container`	Manage containers
* `docker exec`	Run a command in a running container
* `docker inspect`	Return low-level information on Docker objects
* `docker kill`	Kill one or more running containers
* `docker logs`	Fetch the logs of a container
* `docker ps`	List containers
* `docker pull`	Pull an image or a repository from a registry
* `docker rm`	Remove one or more containers
* `docker run`	Run a command in a new container
* `docker start`	Start one or more stopped containers
* `docker stop`	Stop one or more running containers

---

## Docker Compose

---

![docker-image](http://i.imgur.com/3bRKW7u.png?1){:class="img-responsive"}

A tool to defining and running complex applications with *Docker*. It is useful to *compose* more than one docker containers together.
Compose is great for development, testing, and staging environments, as well as CI workflows.

A `docker-compose.yml` might look like below

```dockerfile
version: '3.1'  # if no version is specificed then v1 is assumed. Recommend v2 minimum

services:  # containers. same as docker run
  servicename: # a friendly name. this is also DNS name inside network
    image: # Optional if you use build:
    command: # Optional, replace the default CMD specified by the image
    environment: # Optional, same as -e in docker run
    volumes: # Optional, same as -v in docker run
  servicename2:

volumes: # Optional, same as docker volume create

networks: # Optional, same as docker network create
```

Docker composer config options

|  build |  environment |  image |
|----    |         ---- |             ---- |
| __networks__ |  __volumes__ | __ports__  |

Docker compose commands

* `docker-compose build`
* `docker-compose up`
* `docker-compose down`
* `docker-compose logs`
* `docker-compose ps`
* `docker-compose stop`
* `docker-compose start`
* `docker-compose rm`

A sample docker compose example [docker-lemp](https://github.com/irfanbaigse/docker-lemp){:target="_blank"}

---

## Reference

---

[Docker Docs][docker]{:target="_blank"}

[docker]: https://docs.docker.com
[1]: https://docs.docker.com

---

If you have any questions or comments, feel free to write here or on twitter @irfanbaigse.

---
