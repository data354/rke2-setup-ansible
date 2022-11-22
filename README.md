# rke2-setup-ansible

#### Architecture

#### Prerequises

* **Nodes**

  * At least 3 control planes
  * Many node as data plane are permitted
  * An external machine for backup
  * Ram: 16+ Gi
  * CPU: 8+
  * Disk: 100+ SSD
  * OS: RHEL 7.8/8.5 - Ubuntu 20.04+ - Centos 7
* **Network**

  * All node must be in the same private network
  * Nodes in the k8s cluster are not accessible via Internet
  * Nodes in the k8s cluster are only accessible via the proxy machine (Master ansible)
  * All node have access to Internet via port 443
  * The master ansible host (proxy & load balancer) is accessible via Internet
* **Machine Access**

  * The proxy (Load balancer) machine is accessible via SSH port 22
  * All host in the k8s cluster are accessible via the proxy machine
  * All machine must have an user with root privileges
  * Master ansible public key must be copied on each machine of the k8s cluster to avoid typing password during playbooks execution
