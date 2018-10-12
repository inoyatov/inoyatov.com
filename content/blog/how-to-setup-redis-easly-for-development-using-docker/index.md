---
title: "How to setup Redis easly for development using docker"
date: 2018-10-12T14:00:00+09:00
author: "Khamidulla Inoyatov"
tags:
- Ubuntu 18.04 LTS
- Docker
- Redis
---

* [Prerequisites](#prerequisites)
* [Install Redis](#install-redis)

***

# <a name="prerequisets"></a>Prerequisites

In order to install Redis using docker following requirements must be met:

{{< highlight language="text" >}}
$ docker --version
Docker version 18.06.0-ce, build 0ffa825
$ docker-compose --version
docker-compose version 1.22.0, build f46880fe
{{< /highlight >}}

# <a name="nstall-redis"></a>Install Redis

Open terminal (<kbd>Ctrl+Alt+t</kbd> shortcut to open terminal), and navigate to path where you want to create
docker compose project for Redis. Create *docker-compose.yml* file with following content. 

{{< highlight language="yaml" >}}
version: "3"

services:
    redis:
        container_name: redis-4.0.11 
        image: redis:4.0.11
        restart: always
        ports:
            - "6379:6379/tcp"
{{< /highlight >}}

If you noticied we are binding **6379/tcp** port to external port. If you want to control port by firewall you
should remove ports options from docker compose. Which will limit Redis service to local machine and other docker
containers. Moreover if you want to prevent anonymous access to Redis server you can provide password as following example:

{{< highlight language="yaml" >}}
version: "3"

services:
    redis:
        container_name: redis-4.0.11 
        image: redis:4.0.11
        restart: always
        command: redis-server --requirepass <password>
        ports:
            - "6379:6379/tcp"
{{< /highlight >}}

Finally in order to start and stop Redis server in background following command can be executed:

{{< highlight language="text" >}}
$ docker-compose up -d
$ docker-compose down 
{{< /highlight >}}

if you will not provide **`-d`** option Redis container will be lunched in foreground. That's all Folks!
