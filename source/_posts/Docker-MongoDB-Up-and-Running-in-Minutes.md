---
title: Docker - MongoDB Up and Running in Minutes
draft: true
date: 2016-09-16 10:06:39
categories:
- tools
- database
tags:
- docker
- mongodb
---

Today, I will show steps to pull a MongoDB docker image and locally running a Mongo database server. I have explained in [Docker](docker.html) post the basics and how to configure and run MySQL. 

### Pulling the image
Once you identified the [image](https://hub.docker.com/_/mongo/) , you can bring it to your local machine by issuing the `pull`.
```bash
docker pull mongo:2.2
```

### Starting the MongoDB server
It is good to mount a local drive at `/data/db`, that way DB is available even after server restarts. 
```bash
docker run --name mongodb -v c:/Users/manju/docker/mongo:/data/db -p 27017:27017 -d mongo:2.2 
```
If the server is successfully started, you could see the process information by running the `ps` command. In my case it shows `2ee14feaa563` is the container ID and it is running for the past 6 seconds.  
```
manju@MANJUTHINK C:\workspace\BLOGS
> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                      NAMES
2ee14feaa563        mongo:2.2           "/entrypoint.sh mongo"   18 hours ago        Up 6 seconds        0.0.0.0:27017->27017/tcp   mongodb
03076bd7a501        postgres            "/docker-entrypoint.s"   18 hours ago        Up 31 minutes       0.0.0.0:5433->5432/tcp     pg-server
93f77fd3a7e6        mysql:5.5           "docker-entrypoint.sh"   3 days ago          Up 41 seconds       0.0.0.0:3306->3306/tcp     mp-mysql-server
```

### Connecting to MongoDB server
I use [RoboMongo](https://robomongo.org/) client to interact with MongoDB. Alternately I can connect using mongo shell as shown below:
```bash
docker exec -it 2e bash
mongo
```
The output of a successful connection looks like below:
 ```
manju@MANJUTHINK C:\workspace\BLOGS
> docker exec -it 2e bash
root@2ee14feaa563:/# mongo
MongoDB shell version: 2.2.7
connecting to: test
> show dbs
local   (empty)
> use mytest
switched to db mytest
>
 ```
 
### Conclusion
I did the MongoDB for DBA course a local docker server always help me to brush up my knowledge. Sometime soon I will be doing a post comparing SQL and NoSQL syntaxes. 