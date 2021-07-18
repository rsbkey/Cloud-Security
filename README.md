# Cloud-Security

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![cloud-diagram](/Diagrams/hw-12.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _(Ansible/ansible.yml)_

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
Load balancers help with availability aspect of the servers and also help mitigate against DDOS attacks. 
The advantage of a jump box is to reduce the number of attack vectors (entry points) that hackers have to gain access to the machine. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the configuration files and system logs.
- _TODO: What does Filebeat watch for?_ SSH logings, Linux logins, Sudo commands
- _TODO: What does Metricbeat record?_ CPU, RAM, Network Usage

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1 | Web-server | 10.0.0.5   | Linux            |
| Web-2 | Web-server | 10.0.0.6   | Linux            |
| Elk | Elk Stack| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _My personal IP Address_

Machines within the network can only be accessed by Jump Box.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ Jump Box | IP: 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | My personal IP       |
| Web-1    | Yes                 |                      |
| Web-2    | Yes                 |                      |
| Elk      | No                  | My personal IP       |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _What is the main advantage of automating configuration with Ansible?_
  - To set up manage and deploy multiple servers at the same time. It also reduces the likelihood of human errors and saves us time.

The playbook implements the following tasks:
- _: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
-  Configure Elk VM with Docker
-  Install docker.io
-  Install Docker python module
-  download and launch a docker elk container
-  Enable service docker on boot


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _ List the IP addresses of the machines you are monitoring_
- 10.0.0.5
- 10.0.0.6
- 10.1.0.4

We have installed the following Beats on these machines:
- _Specify which Beats you successfully installed_
- We installed Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- _In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
- Filebeat: Monitors for SSH logins, Linux account logins, and sudo commands
- Metricbeat: Monitors for CPU, RAM, and Network Usage

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the `yaml` file to `/etc/ansible.
- Update the `host` file to include the IP addreses for the webservers you want to change
- Run the playbook, and navigate to `targeted machines` to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
  - The file that is the playbook is the `elk.yml`
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
  - You would update the playbook and the hosts file to run on a targeted machine.
- _Which URL do you navigate to in order to check that the ELK server is running?

https://20.105.23.5:5601


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
