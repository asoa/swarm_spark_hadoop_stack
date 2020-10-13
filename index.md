---
title: "Getting started with spark-hadoop"
keywords: sample homepage
tags: [getting_started]
sidebar: mydoc_sidebar
permalink: index.html
summary: These brief instructions will help you get started quickly with building a docker swarm spark-hadoop stack for big data machine learning
---

## Architecture assumptions

This guide assumes you are building a docker swarm instance using the following high-level architecture:
1. vsphere hypervisor
2. virtual machines for master/secondary nodes (this guide uses vmware photon VMs) [photon](https://vmware.github.io/photon/)


## Software stack
1. docker swarm for container orchestration [docker swarm](https://docs.docker.com/engine/swarm/)
2. apache spark
3. apache hadoop
4. jupyter

## References
1. [hadoop docker-compose config](https://github.com/big-data-europe/docker-hadoop)
2. [spark reference](https://github.com/databricks/Spark-The-Definitive-Guide)
3. [spark swarm reference](https://towardsdatascience.com/a-journey-into-big-data-with-apache-spark-part-1-5dfcc2bccdd2)
4. [spark swarm reference w/ port forwarding](https://blog.newnius.com/setup-distributed-hadoop-cluster-with-docker-step-by-step.html)

{% include links.html %}
