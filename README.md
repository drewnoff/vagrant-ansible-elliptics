vagrant-ansible-elliptics
=========================

Deploying an Elliptics cluster with Ansible 

### Deploy with Vagrant
```shell
vagrant up
```
#### Requirements
* Virtualbox
* Vagrant
* Ansible

### Cluster setup
1. add new hostname into elliptics_servers group in hosts file
2. define variables for the new host in host_vars:
    * node_address_ipv4
    * node_address_port
    * node_monitor_port
    * group
