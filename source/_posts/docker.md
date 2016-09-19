---
title: Docker
date: 2016-02-14 08:32:40
categories:
 - database
tags: 
- docker
- mysql
---
Docker, I am excited!, I am not going to describe what docker is, how it to install it etc. See https://www.docker.com/ for details. Docker is mostly used by software developers and system administrators to quickly setup and manage software or  environment. 
<!-- more -->
### How to use it

With Docker, it is very easy to setup a software in your machine. Wow! thanks to DockerHub, there are a lot of ready-made software containers available. You name it, you will find it there. I can experiment without worrying whether my actions corrupt the software. With few simple commands, I can install or uninstall say a database and run it. 

### Installing MySQL
To begin with, you have to go to https://hub.docker.com/ and search for MySQL. The first search result(https://hub.docker.com/_/mysql/) will take you to the official MySQL server container(s). You can download this prebuilt server by issuing the pull command. 

```bash
docker pull mysql:5.5
```
In order to start MySQL server, you can run the following command
```bash
docker run --name mp-mysql-server -e MYSQL_ROOT_PASSWORD=root123 -e MYSQL_DATABASE=ems -p 3306:3306 -d -v  C:/Users/manju/docker/mysql:/var/lib/mysql mysql:5.5
```

The following command will show the list of running containers. You can obtain the unique identifier for the container from the output.

```bash
docker ps
```

The following command can be used to SSH into a running container. 
```bash
docker exec -it <container-id> bash
```

To stop the container you can use the `stop` or `kill` commands. 
```bash
docker kill <container-id>
```
### How this impacts me

Having a docker powered environment has a positive effect on my QA workflow. For example, I may be asked to validate the install guide of a web application. I can spin off various versions of PostgreSQL or MySQL and point the application to that. 
