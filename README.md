Project 1 Bassett
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _ansible____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: /etc/ansible/pentest.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly effieceint_, in addition to restricting access_ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_ They protect against things like DDOS attacks by shifiting traffic
from server to server, A jumpbox gives access from a single node which is easy to monitor and secure

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the __the data___ and system __logs___.
- _TODO: What does Filebeat watch for?_Filebeat watches for changes in the file system takes note of when and what information has been changed
- _TODO: What does Metricbeat record?_MetricBeat gets teh metric and statistics and ships them to whatever output you choose

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
|Jump Box  | Gateway  | 10.0.0.4   | Linux            |
|Web-1     | Server   | 10.0.0.5   | Linux            |
|Web-2     | Server   | 10.0.0.6   | Linux            |
|Elk-vm    | Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the __Jumpbox___ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _23.151.80.143_

Machines within the network can only be accessed by __10.0.0.4 then go to the ansible container___.
- Jump-box Provsioner(Machine) 10.0.0.4(priv)  40.76.179.72(pub) ?_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 23.151.80.143        |
| Web-1    | No                  | 10.0.0.4 40.76.179.72|
| Web-2    | No                  | 10.0.0.4 40.76.179.72|
| Elk-vm   | No                  | 10.0.0.4 40.76.179.72|
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_You can put commands into multiple servers from a single playbook

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install: docker.io
- Install: python.pip
- Install: docker
- Command: sysctl-w vm.max_map_count-262144
- Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: Web-1 10.0.0.5, Web-2 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_ FileBeat MetricBeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
FileBeat collects the changes done MetricBeat collects metrics and statistics_

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ___pentest.yml__ file to ___/etc/ansible/roles/pentest.yml__.
- Update the __hosts___ file to include destination ip of the elk server 10.1.0.4
- Run the playbook, and navigate to _kibana___ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_/etc/ansible/file/filebeat_config.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
edit the /etc/ansible/host file to add webservers/elkserver ip addr.
- _Which URL do you navigate to in order to check that the ELK server is running? http://52.148.139.221:5601/app/kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
