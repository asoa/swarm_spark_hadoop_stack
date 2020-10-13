---
title: Create Photon VMs
tags: [getting_started]
keywords:
summary: "Use the vmware provided photon images as the platform for the docker swarm runtime"
sidebar: mydoc_sidebar
permalink: mydoc_create_photon_vm.html
folder: mydoc
---

## Architecture assumptions
This guide assumes that the following vsphere archicture exists:
1. VMs--minus photon OS-have been provisioned in the hypervisor environment
2. VMs are tenants of the same port group on physical hosts that belong to a distributed vswitch. This
dependency enables distributed computing across multiple vsphere hosts.  The photon VMs belong
to the `vm` portgroup in the image below.

{% include image.html file="dswitch.png" %}

## Photon OS install
The photon doc site explains the installation of photon os here: [photon install](https://vmware.github.io/photon/assets/files/html/3.0/photon_installation/Running-Photon-OS-on-vSphere.html)

## Photon OS prep for docker swarm
One photon OS is installed, the following system adminstrator tasks are required:
1. Change IP configuration from dhcp to [static](https://vmware.github.io/photon/assets/files/html/3.0/photon_admin/setting-a-static-ip-address.html)
2. Follow the instructions [here](https://vmware.github.io/photon/assets/files/html/3.0/photon_admin/docker-containers.html) to start the docker daemon.
3. Follow the instructions [here](https://docs.docker.com/compose/install/) to install the docker-compose binary
4. Configure the following iptables rules on the `manager` VM:
    * iptables -A INPUT -p tcp --dport 22 -j ACCEPT
    * iptables -A INPUT -p tcp --dport 2376 -j ACCEPT
    * iptables -A INPUT -p tcp --dport 2377 -j ACCEPT
    * iptables -A INPUT -p tcp --dport 7946 -j ACCEPT
    * iptables -A INPUT -p udp --dport 7946 -j ACCEPT
    * iptables -A INPUT -p udp --dport 4789 -j ACCEPT
    * iptables -A INPUT -p tcp --dport 9000 -j ACCEPT
    * iptables -A INPUT -p tcp --dport 50070 -j ACCEPT
5. Configure the following iptables rules on `secondary` VMs:
    * iptables -A INPUT -p tcp --dport 22 -j ACCEPT
    * iptables -A INPUT -p tcp --dport 2376 -j ACCEPT
    * iptables -A INPUT -p tcp --dport 7946 -j ACCEPT
    * iptables -A INPUT -p udp --dport 7946 -j ACCEPT
    * iptables -A INPUT -p udp --dport 4789 -j ACCEPT
    * iptables -A INPUT -p tcp --dport 9000 -j ACCEPT
6. Persist the iptables changes
```
iptables-save >/etc/systemd/scripts/ip4save
```
7. Install make
```
tdnf -y install make
```

## Clone the docker-hadoop repository
```
git clone https://github.com/asoa/hadoop_swarm
```

{% include links.html %}
