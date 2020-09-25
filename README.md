# Project 1

The files in this repository were used to configure the network depicted below.

![Red team network topology](https://github.com/bryce-2020/Project1/blob/master/images/project_1_Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the 'filebeat-playbook.yml' file may be used to install only certain pieces of it, such as Filebeat.

  install_elk.yml, filebeat-config.yml, metricbeat-config.yml, filebeat-playbook.yml, metricbeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting un authorized access to the network.
The main purpose of the load balancer is to help ensure the network has redundancy.

The purpose of the jump box is to have access to the a limited network with access only through a sing IP and machine.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Log data and system Statistics.
What does Filebeat watch for? System Logs
What does Metricbeat record? 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux  |
| Web-1     | Webservers | 10.0.0.5  | Linux |
| Web-2     | Webserver   | 10.0.0.6  | Linux |
| Web-3     | Webserver   |  10.0.0.9 | Linux |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ELK Server machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: Dynamic IP 198.233.230.170

Machines within the network can only be accessed by SSH.
as its IP address: 10.0.0.7

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No       | 10.0.0.7/16       |
| Web-1      | No              |  10.0.0.5/16      |
| Web-2      | No              |  10.0.0.6/16      |
| Web-3      | No              |  10.0.0.9/16      |
| ELK         | Yes/No        |  10.1.0.4/24 |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The advantages of using Ansible, it allows quick deployment of applications or containers. It also has a function of instead of writing specific code per machine you can wite a playbook and apply it to all machines in the resource group.

The playbook implements the following tasks:
Install the pip3 file, install ansible docker python module to increase the virtual memory of the ELK VM then tell the ELK VM to use that new allocated memory. Finally launch the elk docker container.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Sudo Docker ps](https://github.com/bryce-2020/Project1/blob/master/images/sudo_docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 10.0.0.5 Web-2 10.0.0.6 Web-3 10.0.0.9

We have installed the following Beats on these machines:
The beats installed were Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
Metricbeat collects statistics of the systems, and checks services that run on a server. This can be analyzed using the tool kibana. Filebeat also collects data like metricbeat but filebeat collects event log data which then you can authenticate its data integrity.  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/Files1.
- Update the hosts file to include the IP adresses of the VMs you want to run the playbooks.
- Run the playbook, and navigate to kibana to check if the installation worked.

this is the kibana URL where you can check the ELK data.
http://40.71.89.218:5601/app/kibana
![Kibana](https://github.com/bryce-2020/Project1/blob/master/images/kibana_systemlog_success.png.PNG)

### Downloadable Playbook commands
filebeat-config.yml 'curl https://github.com/bryce-2020/Project1/blob/master/Ansible_YML_Scripts/filebeat-config.yml > /etc/ansible/Files1/filebeat-config.yml

metricbeat-config.yml 'curl https://github.com/bryce-2020/Project1/blob/master/Ansible_YML_Scripts/metricbeat-config.yml > /etc/ansible/Files1/metricbeat-config.yml

filebeat-playbook.yml 'curl https://github.com/bryce-2020/Project1/blob/master/Ansible_YML_Scripts/filebeat-playbook.yml > /etc/ansible/roles/filebeat-playbook.yml

metricbeat-playbook.yml 'curl https://github.com/bryce-2020/Project1/blob/master/Ansible_YML_Scripts/metricbeat-playbook.yml > /etc/ansible/Files1/metricbeat-playbook.yml

install-elk.ym 'curl https://github.com/bryce-2020/Project1/blob/master/images/install-elk.yml > /etc/ansible/Files1/install-elk.yml



        
