## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Images/Elk_Cloud_Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the elk_playbookk.yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:

Description of the Topologu
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting downtime to the network.

What aspect of security do load balancers protect?

Load balancers help protect against distributed denial-of-service attacks (DDoS) by adding resiliency by rerouting live traffic from one server to another if it becomes unavailable. In this way, load balancers help to eliminate single points of failure.
What is the advantage of a jump box?

Allows for the most ease of access in working with the environment. You can easily get directly to any server in your environment via SSH
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to machine and system logs.

What does Filebeat watch for?

Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
What does Metricbeat record?

Metricbeat is used to monitor and analyze system CPU, memory and load. In Dockerized environments, Metricbeat can be installed on a host for monitoring container performance metrics.
The configuration details of each machine may be found below.

Name	Function	IP Address	Operating System
Elk Sever	Gateway	10.0.0.4	Linux
DMV1	Docker	10.0.0.5	Linux
DMV2	Docker	10.0.0.6	Linux
Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jump Server machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

107.2.72.218, 73.164.95.23
Machines within the network can only be accessed by Jump Server.

My Elk Server is on my JumpBox Sever so the IP address is 10.0.0.4
A summary of the access policies in place can be found in the table below.

Name	Publicly Accessible	Allowed IP Address
Allow SSH form my laptop	Yes	107.2.72.218, 73.164.95.23
Allow from JumpServer	Yes	10.0.0.4
Allow Elk to the internet	Yes	10.0.0.5, 10.0.0.6
Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

TODO: What is the main advantage of automating configuration with Ansible?
The playbook implements the following tasks:

Install Docker
Increase max map count using sysctl vm.max_map_count
Pull this image from the Docker registry, open a shell prompt and enter
Run a container from the image (elk sebp/elk)
Start up Elk container
Check to see if to see if Kibana's web interface is up and running (e.g. will use http://:5601/)
The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

(Images/docker_ps_output.png)

Target Machines & Beats

This ELK server is configured to monitor the following machines: List the IP addresses of the machines you are monitoring

10.0.0.5
10.0.0.6
We have installed the following Beats on these machines: DMV1 DMV2

Specify which Beats you successfully installed

Filebeats
Metricbeats
These Beats allow us to collect the following information from each machine:

Filebeats: Filebeat monitors the log files. It monitors log files from very specific files, such as those generated by Apache, Microsoft Azure tools, the Nginx web server, and MySQl databases.

Metricbeat: Metricbeat is used to monitor and analyze system CPU, memory and load. They send the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the filebeat-configuration.yml file to /user/ansible/files/filebeat.yml
Update the filebeat.yml file to include the webservers IP address 10.0.0.5 10.0.0.6
Run the playbook, and navigate to http://[your.VM.IP]:5601. to check that the installation worked as expected.
