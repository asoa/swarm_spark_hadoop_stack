---
title: Create Stack
tags: [getting_started]
keywords:
summary: "Create a spark hadoop docker swarm stack"
sidebar: mydoc_sidebar
permalink: mydoc_create_stack.html
folder: mydoc
---

## Assumptions
1. docker swarm created with the following nodes:
  * swarm-mgr (master node)
  * swarm-host1
  * swarm-host2
  * swarm-host3

2. cloned this [repo](https://github.com/asoa/hadoop_swarm.git) to local directory

3. local directory should look like the tree below:
{% include image.html file="tree.png" %}

## Build stack
1. From the directory that the repo was cloned to, run  ```make stack_up```
{% include image.html file="stack_up.png" %}

2. Check the status of the stack using  ```docker service ls```
{% include image.html file="docker_service.png" %}
