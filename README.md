## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Check Diagrams Folder

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
- Load balancers protect the servers from overloading and advantage of a jumpbox is control access and devices to the network.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- Filebeat watches for data that has been changed and when the change took place.
- Metricbeat records metrics and statistics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| JumpBoxProvisioner | Gateway  | 10.0.0.1   | Linux            |
| Web-1              | Server   | 10.0.0.5   | Linux            |
| Web-2              | Server   | 10.0.0.6   | Linux            |
| Web-3              | Server   | 10.0.0.7   | Linux            |
| ShakaMeVM          | Server   | 10.1.0.4   | Linux            |

##4 Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- IP: 52.229.31.171
- Machines within the network can only be accessed by JumpBoxProvisioner VM.
- JumpBoxProvisioner allows access to the ELK VM. IP address is 10.1.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| JumpBoxProvisioner | Yes             | 52.229.31.171    |
| Web-1              | No              | 10.0.0.5         |
| Web-2              | No              | 10.0.0.6         |
| Web-3              | No              | 10.0.0.7         |
| ShakaMeVM          | No              | 10.1.0.4         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The advantage of automating configuration with Ansible is to minimize potential errors and saves time to run playbooks.

The playbook implements the following tasks:
- Install docker.io
- Install python-pip
- Install docker container
- Docker conatiner : Elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

- Check Images Folder for docker ps screenshot

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6
- 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat forwards and centralizes log data. Information is forwarded to Kibana to simplify data. Metricbeat provides and transforms metric data from operating system and servers. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible.
- Update the hosts file to include webservers IPs and elk server IP with syntax ansible_python_interpreter=/usr/bin/python3
- Run the playbook, SSH into the ELKVM and run docker ps to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
- Playbook is install_elk.yml and copy to /etc/ansible
- The file you update hosts files, and install-elk.yml file to run playbook on a certain machine and run ansible-playbook to confirm it us running 
- To specify which machine to install is install-ELK.yml get installed in your ELKServer and Filebeat and Metricbeat get installed in you Webservers.
-  URL to run on your web browser is http://[your.ELK-VM-IP]:5601/app/kibana
