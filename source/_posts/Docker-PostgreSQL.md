---
title: Docker - PostgreSQL
draft: true
date: 2016-02-16 10:05:52
categories:
- database
tags:
- docker
- postgresql
---

In this post, I will briefly explain the steps to getup and running PostgreSQL docker image. I have explained in [Docker](docker.html) post the basics and how to configure and run MySQL. 

### Identifying the Image
Let's begin by searching on [DockerHub](https://hub.docker.com/search/?isAutomated=0&isOfficial=0&page=1&pullCount=0&q=postgresql&starCount=0) and pick the official PostgreSQL version. 
```bash
docker pull postgresql:9
```
If the pull is successful, you must see `postgresql` in the list of docker images. 
```
manju@MANJUTHINK C:\workspace\BLOGS
> docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
mysql               5.5                 89f8142697a0        10 days ago         255.8 MB
mongo               latest              48b8b08dca4d        2 weeks ago         366.4 MB
postgres            9                   6f86882e145d        2 weeks ago         265.9 MB
mongo               2.2                 8558fe135d54        5 months ago        236.9 MB
```

### Start PostgreSQL
The official [documentation](https://hub.docker.com/_/postgres/) touch up on the configuration parameters that are available. Let's start the server now by exposing it on laptop port 5433. 
```
docker run --name pg-server -e POSTGRES_PASSWORD=postgres  -v C:/Users/manju/docker/pg:/var/lib/postgresql/ -p5433:5432 -d postgres
```

### Connecting to Server
There are many ways to connect, I usually use PGAdmin. The following commands you can run to run `psql` from server container. 
```bash
docker ps  # to obtain the container id

docker exec -it <replace-container-d> bash

psql

```

### Conclusion
Docker makes it really easy to install software on demand. In my opinion Docker is a must have tool in a Test Engineers arsenal.  