## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project1 Diagram](C:\Users\jhewl\Documents\Cybersecurity-Bootcamp\GitHub\Project-1\Diagrams\Project1 Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

![elk playbook](C:\Users\jhewl\Desktop\elk playbook.png)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable and available, in addition to restricting traffic to the network.
- Load balancers can defend an organization against denial-of-service (DDos) attacks. The advantage of having a jumpbox is being able to use a virtual machine that has hardended security and can manage other systems within your security sone or overal network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- Filebeat monitors the log files or locations that you specify.
- Metricbeat records the metrics and statistics from the operation system and from services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function   | IP Address | Operating System |
| -------- | ---------- | ---------- | ---------------- |
| Jump Box | Gateway    | 10.0.0.1   | Linux            |
| Lab-1    | Webserver1 | 10.0.0.7   | Linux            |
| Lab-2    | Webserver2 | 10.0.0.5   | Linux            |
| Lab-3    | Webserver3 | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 75.187.107.67

Machines within the network can only be accessed by Jump-Box-Provisioner
- Jump-Box-Provisioner 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
| -------- | ------------------- | -------------------- |
| Jump Box | No                  | 75.187.107.67        |
| ELK      | No                  | 10.0.0.4             |
| Lab-1    | No                  | 10.0.0.4             |
| Lab-2    | No                  | 10.0.0.4             |
| Lab-3    | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible allows IT administrators to automate their daily tasks and save a lot of time. That frees them to focus on efforts that help deliver more value to the business by spending time on more important tasks.

The playbook implements the following tasks:
- Install Docker
- Install python3-pip
- Install Docker python module
- Set the vm.max_map_count to 262144
- Download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![elk server](C:\Users\jhewl\Documents\Cybersecurity-Bootcamp\GitHub\Project-1\Ansible\elk server.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Lab-1 **10.0.0.7**
- Lab-2 **10.0.0.5**
- Lab-3 **10.0.0.6**

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the log files or locations that you specify, which we use to see what changes or messages the log files have received such as kill commands. Metricbeat records the metrics and statistics from the operation system and from services running on the server, which we could use to look at how much RAM or CPU usage was being used on the webservers at certain time.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible.cfg file to /etc/ansible

- Update the hosts file to include

  [elk]

  10.1.0.4 ansible_python_interpreter=/usr/bin/python3

- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected

_TODO: Answer the following questions to fill in the blanks:_
- Copy the install-elk.yml and filebeat-playbook.yml file to /etc/ansible
- Update the install-elk.yml and filebeat-playbook.yml file to include the machine you want use the playbooks on by changing the hosts name on the 3rd line.
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

### Commands to Use the Playbook

- nano ansible.cfg
- add the machine, its IP, and ansible_python_interpreter=/usr/bin/python3 to the hosts
- Ctrl + x to exit file
- in the folder that install-elk.yml is in, run: cp install-elk.yml /etc/ansible
- nano install-elk.yml /etc/ansible
- name: installing elk hosts: [your_machine]
- Ctrl + x to exit file
- ansible-playbook install-elk.yml