## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!(/Images/Azure-Network-Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the  file may be used to install only certain pieces of it, such as Filebeat.

  (ProjectFiles/elk-playbook.yml)
  (ProjectFiles/filebeat-install.yml)

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

Load balancers protect the availability aspect of security.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the application and system files.

The configuration details of each machine may be found below.


| Name       | Function   | IP Address | Operating System |
|------------|------------|------------|------------------|
| RedOne     | Jump Box   | 10.0.0.4   | Linux            |
| Web-1      | Web Server | 10.0.0.6   | Linux            |
| Web-2      | Web Server | 10.0.0.5   | Linux            |
| DVWA-VM2   | Web Server | 10.0.0.7   | Linux            |
| Elk Server | ELK Server | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 24.10.155.112

Machines within the network can only be accessed by RedOne.
- 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses    |
|------------|---------------------|-------------------------|
| RedOne     | Yes                 | 24.10.155.112           |
| Web-1      | No                  | 10.0.0.4                |
| Web-2      | No                  | 10.0.0.4                |
| DVWA-VM2   | No                  | 10.0.0.4                |
| Elk Server | Yes                 | 24.10.155.112 10.0.0.4  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- Everything is configured the exact same way, every time.

The playbook implements the following tasks:

- Install Docker
- Install Python 3
- Download ELK Docker image

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

- 10.0.0.5
- 10.0.0.6
- 10.0.0.7

We have installed the following Beats on these machines:

- Filebeat

These Beats allow us to collect the following information from each machine:
- The system logs for our webservers.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk-playbook.yml file to /etc/ansible/files.
- Update the /etc/ansible/hosts file to include the elk group and add the target vm's ip address to that group
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.


(Images/kibana.png)
