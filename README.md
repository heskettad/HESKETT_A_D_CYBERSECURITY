# HESKETT_A_D_CYBERSECURITY
Projects and scripts for Dean Heskett
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Azure Data Center w Virtual Machines and ELK Server (Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Azure Data Center file may be used to install only certain pieces of it, such as Filebeat.

  -filebeat-config.cfg
  -filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly functional, in addition to restricting excess traffic to the network.
What aspect of security do load balancers protect?
	-The load balancer will ensure smooth functioning during high traffic situations. The uptime will be more stable, as well as providing multiple redundences to ensure stable operation.

What is the advantage of a jump box?
	-The jumpbox is a secured workstation that is only accessed by a specific ssh key and ip address. This hardens the jumpbox and network from malicious attacks and other security threats.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
-What does Filebeat watch for?
	-Filebeat monitors specific log files and sends them to Elasticsearch for indexing.

What does Metricbeat record?
	-Metricbeat collects data that can then be outputed to Elasticsearch or Logstash.

The configuration details of each machine may be found below.

| Name               | Function | IP Address | Operating System |
|--------------------|----------|------------|------------------|
| JumpBoxProvisioner | Gateway  | 10.0.0.4   | Linux            |
| Web-1              | VM Server| 10.0.0.6   | Linux            |
| Web-2              | VM Server| 10.0.0.7   | Linux            |
| ELK-1              |ELK Server| 10.1.0.4   | Linux            |
| Web-3		     | VM Server| 10.0.0.5   | Linux
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 69.212.60.44 whitelisted IP address

Machines within the network can only be accessed by the JumpBoxProvisioner.
-Which machine did you allow to access your ELK VM?
-JumpBoxProvisioner

What was its IP address?
-40.118.213.25 (Public)
-10.0.0.4      (Private)

A summary of the access policies in place can be found in the table below.

| Name               | Publicly Accessible | Allowed IP Addresses |
|--------------------|---------------------|----------------------|
| JumpBoxProvisioner | Yes                 | 69.212.60.49         |
| Web-1              | No                  | 10.0.0.4             |
| Web-2 	     | No		   | 10.0.0.4		  |
| ELK-1              | No                  | 10.0.0.4             |
| Web-3		     | No                  | 10.0.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-What is the main advantage of automating configuration with Ansible?
	-Time savings and automation of tasks.
	-Fewer errors and mistakes

The playbook implements the following tasks:
-ssh into the JumpBoxProvisioner to access the servers and begin installation
-Start and attach docker file within Ansible
-Create ELK playbook withing /ansible/roles
-Run ELK playbook
-ELK server is up an running

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/heskettad/HESKETT_A_D_CYBERSECURITY/blob/main/diagrams/Screenshot%202022-03-18%20161821%20elk.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-Web-1 (10.0.0.6)
-Web-2 (10.0.0.7)
-Web-3 (10.0.0.5)

We have installed the following Beats on these machines:
-Filebeat and Metricbeat were successfully installed on Web-1, Web-2, and Web-3

These Beats allow us to collect the following information from each machine:
-Filebeat
	-Looks for specified log data in designated locations
	-Harvests this log data and sends it to libbeat
	-Libbeat aggregates this data and sends to designated output

-Metricbeat
	-Collects machine metrics, ex. uptime
	-All dada can be collected and analyzed at a latter time



### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/ansible/roles/files.
- Update the filebeat-config.yml file to include the ip address and port# of the ELK machine (10.1.0.4:9200) Line #1106, Replace ip address on Line#1806 with ELK machine ip and port# (10.1.0.0.4:55601)
- Run the playbook, and navigate to 20.231.45.226:5601 to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- Which file is the playbook? 
	-filebeat-playbook.yml
-  Where do you copy it? 
	-/etc/ansible/roles
- _Which file do you update to make Ansible run the playbook on a specific machine?
	-/etc/ansible/hosts, specify ip of machine
 How do I specify which machine to install the ELK server on versus which to install Filebeat on?
	-one machine is webservers with Filebeat, the other is elkservers with metric beat	
- Which URL do you navigate to in order to check that the ELK server is running?
	-http://20.231.45.226:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._











