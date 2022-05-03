## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Alt text](https://github.com/Vh8g52Dk3/ELK-PROJECT-1/blob/main/DIAGRAMS/PROJECT-1%20DIAGRAM.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function        | IP Address | Operating System |
|----------|-----------------|------------|------------------|
| Jump Box | Gateway         | 10.0.0.4   | Linux            |
| WEB1     | Web Server      | 10.0.0.5   | Linux            |
| WEB2     | Web Server      | 10.0.0.6   | Linux            |
| ELK      | Elastic Search  | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 5.188.123.233

Machines within the network can only be accessed by the jumpbox.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?
- Jumpbox:
-   Public IP:  20.210.96.156
-   Private Ip: 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP Addresses           |
|---------------|---------------------|--------------------------------|
| Jump Box      |  No                 | Workstation Public IP -p 22    |
| WEB1          |  No                 | 10.0.0.4 -p 22                 |
| WEB2          |  No                 | 10.0.0.4 -p 22                 |
| Load Balancer |  No                 | Workstation Public IP -p 80    |
| ELK           |  No                 | Workstation Public IP -p 5601  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because 
What is the main advantage of automating configuration with Ansible?

-It reduces errors when setting the configurations

-Errors were reduced when setting the configurations.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

-Download and Launch Elk Container - specified ports
-Install Docker - docker.io
-Increase Memory
-Install pip3 - python3-pip

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
- Filebeat and Metricbeat was installed on Web-1 and Web-2


These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

- Filebeat allows us to collect system events such as logins.
- Metricbeat allows us to collect metrics such as cpu and memory usage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk.install.yml file to /etc/ansible/elk_install.yml.
- Update the host file to include:
-   [elk]
-   10.1.0.1 ansible_python_intrepreter=usr/bin/python3

- Run the playbook, and navigate to http://[elk-server-ip]:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?  Copy install_elk.yml to /etc/ansible/install_elk.yml in your Jumpbox Ansible Container
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?  Run Playbook: ansible-playbook /etc/ansible/install_elk.yml
- _Which URL do you navigate to in order to check that the ELK server is running?  Check to see http://[elk-server-ip]:5601/app/kibana is running.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

root@051c9edebe77:etc/ansible# nano hosts
ansible-playbook filebeat-playbook.yml
