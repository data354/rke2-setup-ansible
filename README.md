# rke2-setup-ansible

### Description

This project is the setup of a production environment based on a kubernetes cluster for the deployment of a Big Data stack. It automates the setup of a highly available k8s cluster on the RKE2 distribution and the installation of all software stacks.

It takes into account the following features:

* Scaling (up and down)
* Load balamcer et proxy
* Nodes Security
* Backup (Etcd and PV)
* Multiple OS family (Debian and Redhat)
* Idempotence

### Architecture


### Prerequises

* **Nodes**

  * An odd number of control plane (minimum 3)
  * Many node as data plane are permitted
  * An machine as load balancer and proxy
  * An external machine for backup
  * Ram: 16+ Gi
  * CPU: 8+
  * Disk: 100+ SSD
  * OS: RHEL 7.8/8.5 - Ubuntu 20.04+ - Centos 7
* **Network**

  * All node must be in the same private network except the backup node
  * Nodes in the k8s cluster are not accessible via Internet
  * Nodes in the k8s cluster are only accessible via the proxy machine (Master ansible)
  * All node have access to Internet via port 443
  * The master ansible host (proxy & load balancer) is accessible via Internet
* **Machine Access**

  * The proxy (Load balancer) machine is accessible via SSH port 22
  * All host in the k8s cluster are accessible via the proxy machine on port SSH port 22
  * All machine must have a same user with root privileges (proxy and backup machine include)
  * Master ansible public key must be copied on each machine of the k8s cluster to avoid typing password during playbooks execution

### Process
