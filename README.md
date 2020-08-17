## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](https://github.com/haleya1999/ELK-Project/blob/master/Diagrams/NetworkDiagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - [Ansible yml files](https://github.com/haleya1999/ELK-Project/blob/master/Ansible)


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.


The configuration details of each machine may be found below.

| Name | Function | IP Address | OperatingSystem |
|-|-|-|-|
| Jump Box | gateway | 10.0.0.9 | ubuntu |
| Web 1 | web server | 10.0.0.7 | ubuntu |
| Web 2 | web server | 10.0.0.4 | ubuntu |
| Elk Machine | log server | 10.1.0.4 | ubuntu |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 45.31.112.159

Machines within the network can only be accessed by the Jump box with the IP address 10.0.0.9.


A summary of the access policies in place can be found in the table below.

| Name | Publicly accessible | Allowed IP Address |
|-|-|-|
| Jump Box | Yes | 45.31.112.159 |
| Web 1 | No | 10.0.0.9 |
| Web 2 | No | 10.0.0.9 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because there is less room for human error and confuguration of multiple machines can take minutes.

The playbook implements the following tasks:
- Increase the memory to 262144
- Make sure the memory is 262144 on restart
- Install Docker
- Install Python3
- Download Image

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![screenshot of docker ps output](https://github.com/haleya1999/ELK-Project/blob/master/Linux/docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:  
 - IP address 10.0.0.7 (Web 1)
 - IP address 10.0.0.4 (Web 2)

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- 
`Filebeat` collects log files, we could expect to see auth log and syslog data. `Metricbeat` collects system metrics, we could expect to see memory and cpu data

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ELK playbook file to /etc/ansible.
- Update the configuration file to include [elk]
'Internal IP' ansible_python_interpreter=/usr/bin/python3
- Run the playbook, and navigate to http://`ELKPublicIP`:5601/app/kibana to check that the installation worked as expected.

