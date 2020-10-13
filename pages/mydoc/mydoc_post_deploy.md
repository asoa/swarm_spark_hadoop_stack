---
title: Create Stack
tags: [getting_started]
keywords:
summary: "Stack post-deployment tasks"
sidebar: mydoc_sidebar
permalink: mydoc_post_deploy.html
folder: mydoc
---

## Assumptions
1. Stack was deployed using ```make stack_up```

## Expose stack services externally using port forwarding
1. Refer to this [blog](https://blog.newnius.com/setup-distributed-hadoop-cluster-with-docker-step-by-step.html) for context.  
2. We use a socat process from a docker container described in the blog above to fork network streams from the docker swarm [overlay](https://docs.docker.com/network/overlay/) network and expose them to the local host--I know cray huh? So, for the spark-master docker instance that is inaccessible to the world, we create the a container (newnius/port-forward) that is sort of dual-homed and looks like this:

```
(docker host) <-[socat process]- (newnius/port-forward) -[docker swarm overlay network]-> (spark-master)
```
The (docker host) is accessible to us from the vsphere environment, so we can connect to ```localhost:<spark-master port>``` to access the spark-master service

The docker service command below creates the socat process described above
{% include image.html file="port_fwd_master.png" %}
