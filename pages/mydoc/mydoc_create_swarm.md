---
title: Create Swarm
tags: [getting_started]
keywords:
summary: "Create a docker swarm"
sidebar: mydoc_sidebar
permalink: mydoc_create_swarm.html
folder: mydoc
---

## Create docker Swarm
Use the instructions [here](https://docs.docker.com/engine/swarm/swarm-tutorial/create-swarm/) to create a swarm.
Verify the swarm by running ```docker node ls```
{% include image.html file="swarm_nodes.png" %}

## Create local swarm registry to distribute images built from docker-compose
```
docker run -d -p 5000:5000 --restart=always --name registry registry:2
```

## Clone repo to swarm manager and build containers
1. Clone this [repo](https://github.com/asoa/hadoop_swarm.git) and ensure the *.sh files
are executable (chmod +x) in your environment
2. Run ```make build_hadoop``` and ```make build_spark``` to build containers
3. After containers are built, running ```docker images``` should return something like this:
{% include image.html file="docker_images.png" %}
