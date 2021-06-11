# Project_1_ELK
Project 1 Week 13 Elk Stack
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

-See Playbook Directory for the setup files

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly availible, in addition to restricting inbound access  to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.
Filebeat detects changes to the filesystem. Specifically, we use it to collect Apache logs.
 Metricbeat detects changes in system metrics, such as CPU usage. We use it to detect SSH login attempts, failed sudo escalations, and CPU/RAM statistics.

The configuration details of each machine may be found below.

| Name     | Function | IP       | OS    |   |
|----------|----------|----------|-------|---|
| Jump Box | Gateway  | 10.0.0.7 | Linux |   |
| Web1     | Websever | 10.0.0.5 | Linux |   |
| Web2     | Websever | 10.0.0.6 | Linux |   |
| Elk      | Monitor  | 10.1.0.4 | Linux |   |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: Host Machine Ip


Machines within the network can only be accessed by ssh from the Jump Box.

A summary of the access policies in place can be found in the table below.

|| Name | Publicly Accessible | Allowed IP Addresses |
|------|---------------------|----------------------|
| Jump | yes                 | Host Machine Only    || Web1 | no                  | 10.0.0.0/24          |
| Web2 | no                  | 10.0.0.0/24          |
| Elk  | no                  | 10.0.0.0/24          |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the process is repeatable and free of possible human error while also being significantly faster.


The playbook implements the following tasks:
- installs docker, pip3, and docker module
- Increase memory for the ELK vm
- download and launch docker container on elk server

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.5 & 10.0.0.6, Web1 & Web2 respectively. 

We have installed the following Beats on these machines:
Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects and monitors log files on the system. The system logs of the Websevers, viewed through kibana is an example of filebeat in use.
- Metricbeat collects system data and performance which can be used as a litmus for system health. Monitoiring the cpu usage eould be one such example.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configuration file to the web containers.
- Update the hosts file to include IPs of websevers and Elk sever.
- Run the playbook, and navigate to http://[Elk_VM_Public_IP]:5601/app/kibana to check that the installation worked as expected.


- _Which file is the playbook? Where do you copy it? The Filebeat-configuration,  /etc/ansible/files/filebeat-config.yml to /etc/filebeat/filebeat.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? Edits to the filbeat-config.yml will allow you to specify the ip addresses that you want configured. As listed above, adding our Websevers and Elk sever to that config file allows the automatic setup.
- http://23.101.183.147:5601/app/kibana



