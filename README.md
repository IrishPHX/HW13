# HW13
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](https://github.com/IrishPHX/HW13/blob/main/Diagrams/HW13%20Diagram.jpg?raw=true)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the **anisble playbook** file may be used to install only certain pieces of it, such as Filebeat.

 [Install-ELK](https://github.com/IrishPHX/HW13/blob/main/Ansible/install-elk.yml.txt)
  

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly *available*, in addition to restricting *access* to the network.
- What aspect of security do load balancers protect? - Load balancers help protect against SSL offload, Traffic cashing, Traffic compression, User ID Auths, and the always persistantant DDos or Denilal of Service attacks.

- What is the advantage of a jump box? - A Jump Box is a way to use the interenet to create a single entry point to other machins from a specific IP and then to other machines.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the *log files* and *system resources*.
- What does Filebeat watch for? - Filebeat monitors for log files, collects log events,
- What does Metricbeat record? - Metricbeat records metrics and statistics

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1    |  DVWA    | 10.0.0.6   | Linux            |
| Web-2    |  DVWA    | 10.0.0.7   | Linux            |
| Elk      |  ELK     | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the *Jump Box* machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 70.166.105.137

Machines within the network can only be accessed by *Jump Box*.
- 10.0.0.1

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 70.166.105.137       |
| Web-1    | No                  | 10.0.0.6             |
| Web-2    | No                  | 10.0.0.7             |
| ELK      | No                  | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? - Similar as to Filebeat and Metricbeat, You can input commands into multiple servers from a single playbook


The playbook implements the following tasks:
- Install docker.io
- Install Python3-pip
- Install Docker Python Mod
- Download and launch ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![sudo docker ps](https://github.com/IrishPHX/HW13/blob/main/Diagrams/dockerPS_2.JPG?raw=true)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.6
- Web-2 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat will watch user specified locations or log files and then forward log events to Elasticsearch or Logstash
- Metricbeat collects a stash of metrics from the OS and services running and then ships the results you specified to Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the *playbook* file to */etc/anisble/*.
- Update the *host* file to include the ip address of the elk-stack
- Run the playbook, and navigate to *http://[VM IP]:5601/app/kibana* to check that the installation worked as expected.


