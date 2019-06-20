Please note that these playbooks are provided without support and are intended to be a guideline. Any issues encountered can be reported via the GitHub issues and will be addressed on a best effort basis. Pull requests are also encouraged.

# Introduction

Ansible provides a simple way to deploy, manage, and configure the Confluent Platform services. This repository provides playbooks and templates to easily spin up a Confluent Platform installation. Specifically this repository:

* Installs Confluent Platform packages
* Starts services using systemd scripts
* Provides configuration options for plaintext, SSL, and SASL_SSL communication amongst the services

The services that can be installed from this repository are:

* ZooKeeper
* Kafka
* Schema Registry
* REST Proxy
* Confluent Control Center
* Kafka Connect (distributed mode)

# Documentation

You can find the documentation for running this playbook at https://docs.confluent.io/current/tutorials/cp-ansible/docs/index.html.

## How to use

1. Install Zookeper & Kafka Brooker

 - ansible-playbook -i local-hosts.yml local-zookeeper-kafka.yml -vvv

2. Check services are running

 - systemctl status confluent-* -l
 
3. Install n Brokers

 - ansible-playbook local-kafka.yml -vvv

4. Service will not start

 - systemctl status confluent-* -l

5. Change Zookeeper & kafka configuration files in each new Broker

 - ansible-playbook local-add-broker.yml --extra-vars "zookeeper_id=1 zookeeper_ip=10.159.83.34 brooker_counter=2" -vvv  
 - ansible-playbook local-add-broker.yml --extra-vars "zookeeper_id=1 zookeeper_ip=10.159.83.34 brooker_counter=3" -vvv  
 - etc...  