## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._
  - install-elk.yml
  - https://drive.google.com/file/d/1xq_S9uqWAepGOQbm7_1uUDlSj01lN97A/view?usp=sharing


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Virtual Machines

Jump-box-provisioner/ Ansible
Web-1/ DVWA
Web-2/ DVWA
ELK-VM/ 
### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
-  The aspect of security load balancers protect are availability. By routing client requests across servers capable of fulfilling those requests, maximizing speed and space utilized and ensures that no one server is overflowed: It protects against Distributed Denial-of-service attacks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_
  _TODO: What does Metricbeat record?
- Filebeat collects data from the log files or locations that you specify, collects log events, and forwards them to either  Elasticsearch or an output pf your choice for indexing/storing
-Metricbeat takes the metrics and statistics that collects and ships them to the output you specify

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.5   | Linux            |
| ElK-VM   |ELK SERVER| 10.0.0.4   | Linux            |
| Web-2    |WEB SERVER| 10.1.0.6   | Linux            |
| Web-1    |WEB SERVER| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
- Jump-Box-Provisioner IP : 10.1.0.5 via SSH port 22
- My PC: MypublicIP cia port tcp 5601

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | MypublicIP/my pcIP   |
|    WEB-1 | NO                  | 10.1.0.5             |
|    WEB-2 | NO                  | 10.1.0.5             |
|   ELK-VM | NO                  | 10.1.0.5             |  
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
- ansible will figure out how to automate configuration after youve listed the tasks requred in a playboook using ansible apps. 
The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker.io
- Install Python3-pip
- Intall Docker Module
- Increase Virtual Memory
- Download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[elk](https://user-images.githubusercontent.com/70101639/110220968-e5282000-7e8e-11eb-8f8f-f9b4ed59b0cc.PNG)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring.
*13.83.84.101/10.1.0.4
13.83.84.101/10.1.0.6
40.83.210.207/10.1.0.5
10.0.0.4


We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
 * Filebeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc. 
* Filebeat collects data from the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing/storing.<img width="1266" alt="file beat example" src="https://user-images.githubusercontent.com/70101639/110215883-b2236380-7e71-11eb-9b6f-4d3c351ec9bc.png">


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? /etc/ansible/files/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? 
*
you update the /etc/ansible/host file to add the host used on the specific machine (webservers/elk). To differentiate when in the host file after adding the specfic host group underneath you would specify the machine private ip adreess.
- _Which URL do you navigate to in order to check that the ELK server is running? http://40.88.131.93:5601/ The only thing changing being the ip address which is specific to your elkservers pub. ip-adress

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
*ansible-playbook <name fo playbook.yml>
