## Automated ELK Stack Deployment


The files in this repository were used to configure the network depicted below.


<%/Downloads/README/Images/Network Diagram.png>


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yaml file may be used to install only certain pieces of it, such as Filebeat.


  - install_elk2.yml


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build




### Description of the Topology


The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.


Load balancing ensures that the application will be highly available, in addition to restricting in-bound traffic to the network.


What aspect of security do load balancers protect? 


* A load balancer distributes traffic from clients across multiple servers without clients having to know how many servers are in use or how they are configured. Because the load balancer sits between the clients and the servers it can enhance the user experience by providing additional security, performance, resilience and simplify scaling your website.


What is the advantage of a jump box?


* The jump box is a secure computer that allows all admins to first connect to before launching an administrative task or use as an origination point to connect to other servers.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network.
* What does Filebeat watch for? Filebeat looks for Changes to log files. 
* What does Metricbeat record? Collects metrics from the operating system and services running on the server.


The configuration details of each machine may be found below.


| Name       | Function   | IP Address | Operating System |
|------------|------------|------------|------------------|
| JumpBox    | gateway    | 10.0.0.7   | Linux            |
| Web 1      | webserver  | 10.0.0.8   | Linux            |
| Web 2      | webserver  | 10.0.0.9   | Linux            |
| Elk-Server | monitoring | 10.1.0.4   | Linux            |




### Access Policies


The machines on the internal network are not exposed to the public Internet. 


Only the JumpBox provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
* 107.211.227.235


Machines within the network can only be accessed by the jump box provisioner. Which machine did you allow to access your ELK VM? 
* What was its IP address? 104.211.11.187


A summary of the access policies in place can be found in the table below.


| Name       | Publically accessible | Allowed IP Address |
|------------|-----------------------|--------------------|
| JumpBox    | Yes                   | 107.211.227.235    |
| Web 1      | No                    | 10.1.0.4           |
| Web 2      | No                    | 10.1.0.4           |
| Elk-Server | No                    | 10.1.0.4           |




### Elk Configuration


Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
* Free: Ansible is an open-source tool.
* Very simple to set up and use: No special coding skills are necessary to use Ansible’s playbooks (more on playbooks later).
* Powerful: Ansible lets you model even highly complex IT workflows.
* Flexible: You can orchestrate the entire application environment no matter where it’s deployed. You can also customize it based on your needs.
* Agentless: You don’t need to install any other software or firewall ports on the client systems you want to automate. You also don’t have to set up a separate management structure.
* Efficient: Because you don’t need to install any extra software, there’s more room for application resources on your server.




The playbook implements the following tasks: in 3-5 bullets, explain the steps of the ELK installation play. 
* Install docker.io
* Install pip3
* Install docker python module
* increase virtual memory
* Download and launch a docker 


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


<%/Downloads/README/Docker ps.png>


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
* Private IPs of Web-1 and Web-2


We have installed the following Beats on these machines:
* Microbeat


These Beats allow us to collect the following information from each machine:
* Filebeat - collects data about the file system
* Metricbeat - collects machine metrics, such as uptime




### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 


SSH into the control node and follow the steps below:
* Copy the playbook file to /etc/ansible/.
* Update the hosts file to include IP addresses of machines you want the playbook ran on.
* Run the playbook, and navigate to http://your.elk.public.ip:5601/app/kibana to check that the installation worked as expected.


Answer the following questions to fill in the blanks:_
- Which file is the playbook? install_elk2.yml Where do you copy it? /etc/ansible
- Which file do you update to make Ansible run the playbook on a specific machine? The hosts file
- How do I specify which machine to install the ELK server on versus which to install Filebeat on? In the Elk and filebeat playbooks you will have to give correct hosts name.
- Which URL do you navigate to in order to check that the ELK server is running? http://your.elk.public.ip:5601/app/kibana