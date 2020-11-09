# Maddox
 Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

### <network_diagram.png>

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

- This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system uptime.

The configuration details of each machine may be found below.


| Name     | Function      | IP Address | Operating System |
|----------     |----------        |------------    |------------------|
| Jump Box | Gateway  | 10.0.0.1       | Linux |
| ELK Server| Stack SVR| 10.1.0.4      |Linux   |
| Web 01     |Web SVR  | 10.0.0.9      |Linux   |
| Web 02     |Web SVR  | 10.0.0.10    |Linux   |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JUMPBOX machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
“PUBLIC IP HERE” 


Machines within the network can only be accessed by JUMPBOX IP of 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |       Yes           | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The main benefit is to allow Administrators to automate 
- Playbooks are written in YAML

The playbook implements the following tasks:
- Create a new VM to host the ELK server
- Download and configure the elk-docker container
- Launch the elk-docker container to start the Server
- Configure security group to allow access to the ELK server via HTTP

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

### <docker-ps.png>

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.9 
- 10.0.0.10 

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects data about the file systems. As an example Filebeat can collect data on /var/log/apache2/* which would be used to view Apache Access Logs
- Metricbeat collects machine metrics such as System, MYSQL, and Docker, as an example. 
- Metricbeat is configured to use the system module to collect system metrics like CPU or network. 


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/ansible/roles.
- Configure /etc/ansible/hosts file (while connected to Docker) 
- Update webservers group to include webservers and ELK servers group to include your target ELK server
- Run the playbook, and navigate to  -ELK public-IP:5601/app/kibana 
- to check that the installation worked as expected.

- end
