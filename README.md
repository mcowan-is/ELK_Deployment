# ELK_Deployment
Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Network Diagram

![plot](./ELK_Deployment/Images/diagram.drawio)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.

All playbooks involved are in the repository under Ansible. Playbooks are for

Installing docker
Installing Elk
Installing Filebeat
This document contains the following details:

Description of the Topology
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly scalable, in addition to restricting access to the network.

What aspect of security do load balancers protect?

Load balancers ensure availability of the web application.
What is the advantage of a jump box?

The use of a jump box guarantees a single, secure, point of entry to network resources.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system statistics.

The configuration details of each machine may be found below.

Name	Function	IP Address	Operating System
Jump Box	Gateway	10.0.0.4	Ubuntu 18.04
Web-1	DVWA Container	10.0.0.5	Ubuntu 18.04
Web-2	DVWA Container	10.0.0.6	Ubuntu 18.04
Elk-VM	Elk Stack	10.1.0.4	Ubuntu 18.04
Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 20.37.48.234, or whatever my personal IP address happens to be.

Machines within the network can only be accessed by jump box provisioner.

Which machine did you allow to access your ELK VM? My home PC via port 5601 and the jumpbox provisioner (40.88.51.63) via ssh.

A summary of the access policies in place can be found in the table below.

Name	Publicly Accessible	Allowed IP Addresses
Jump box	no	<Home IP Address>
Web 1	no	40.88.51.63
Web 2	no	40.88.51.63
Elk-VM	no	<Home IP Address> and 40.88.51.63
Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it's at a higher layer of abstraction than a simple startup script, making it easier to debug and maintain.

The playbook implements the following tasks: Install pip3 Install docker.io Install docker Install sebp elk container Sets vm max map count to 262144

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

![plot](./ELK_Deployment/Images/Capture.PNG)

Target Machines & Beats
This ELK server is configured to monitor the following machines: 10.0.0.5 10.0.0.6 10.0.0.7

We have installed the following Beats on these machines: 10.0.0.5 10.0.0.6

These Beats allow us to collect the following information from each machine:

Filebeats collects system logs from the target pc.

Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the install-elk.yml file to /etc/ansible.
Update the hosts file to include the relevant ip address for Elk-VM under the group [elk]
Run the playbook, and navigate to http://<ELK.VM.External.IP>:5601/app/kibana to check that the installation worked as expected.
