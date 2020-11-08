# Cybersecurity-Project



### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
 - What aspect of security do load balancers protect? A load balancer protects servers from traffic overload.  Therefore, it balances traffic between multiple servers
- What is the advantage of a jump box? The main advantage of a Jump Box is its serves as a DMZ that protects the internal networks 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
 
 - What does Filebeat watch for? Filebeat watches for log files and they also collect log events.
 - What does Metricbeat record? Metricbeat records metrics from operating systems that is running on the servers

The configuration details of each machine may be found below. 

| Name     | Function    | IP Address | Operating System |
|----------|-------------|------------|------------------|
| Jump Box | Gateway     | 10.0.0.4   | Linux            |
| Web-1    | DVWA Server | 10.0.0.5   | Linux            |
| Web-2    | DVWA Server | 10.0.0.6   | Linux            |
| Web-3    | DVWA Server | 10.0.0.8   | Linux            |
| Elk      | Elk Stack   | 10.1.0.5   | Linux            |



































### Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 99.76.9.16 which is my home IP address which is access via ssh.  The Jump Box was allowed to access ELK server via ssh from my home IP address

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | My home IP address   |
| Web-1    | Yes                 | 10.0.0.4             |
| Web-2    | Yes                 | 10.0.0.4             |
| Web-3    | Yes                 | 10.0.0.4             |
| Elk      | No                  | 10.1.0.5             |


























### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you minimize the potential of human error and it's easier to configure multiple machines all at once when it’s done automatically.

The playbook implements the following tasks:
- Install docker.io
- Install python3-pip
- Install Docker module
- Increase virtual memory (command: systemctl -w vm.max_map_count=262144)
- Download and configure elk docker container
- Set published ports

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.
Note: The following image link needs to be updated. Replace docker_ps_output.png with the name of your screenshot image file.









### Target Machines & Beats
This ELK server is configured to monitor the following machines:

- Web-1 10.0.0.5
- Web-2 10.0.0.6
- Web 3 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:

- File beat collects data from the file system and then transfers logs to the Elk server.  Kibana is used so you can inspect the log files.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

- Copy the filebeat-config file to /etc/ansible/files.

- Update the config file to include ELK server IP address to the Elastic search output and sections of Kibana

- Run the playbook, and navigate to http://<Elk.VM.External.IP>:5601/app/kibana to check that the installation worked as expected.
 
 Answer the following questions to fill in the blanks:

- Which file is the playbook? Where do you copy it? Install-elk playbook.yml is the file and you would copy it in /etc/ansible

- Which file do you update to make Ansible run the playbook on a specific machine?You will update the filebeat-playbook.  How do I specify which machine to install the ELK server on versus which to install Filebeat on? When you nano in the host file, you will specify what needs to be installed for example ElK server or Filebeat

-_Which URL do you navigate to in order to check that the ELK server is running?
http://publicIP(elkserver):5601

