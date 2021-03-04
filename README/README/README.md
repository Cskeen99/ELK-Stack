## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Images/ELK_Network_Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml

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

- Load balancer protect the availability of the network and data. This allows us to take full advantage of the jump box provisioner by quickly accessing all the virtual machines installed into the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system integrity.
- Filebeat monitors the log files and locations specified by the system administrators. 
- Metricbeat takes the metrics and statistics and collects them into the specified location, in this case, Elasticsearch and Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.







-------------------------------------------------------
| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| ELK-VM   | ELK-stack| 10.1.0.4   | Linux            |
| Web-1    | Webserver| 10.0.0.7   | Linux            |
| Web-2    | Webserver| 10.0.0.6   | Linux            |
| Web-3    | Webserver| 10.0.0.8   | Linux            |
-------------------------------------------------------

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ELK Virtual machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 65.130.1.82

Machines within the network can only be accessed by SSH.

- The machine that controls access to the ELK VM is the ansible container found inside the jump box VM. The IP address for the jump box machine is 52.183.5.55

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 65.130.1.82          |
| ELK-VM   | No                  | 65.130.1.82          |
| Web-1    | yes                 | *                    |
| Web-2    | yes                 | *                    |
| Web-3    | yes                 | *                    |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The amount of time saved from performing general and boilerplate configurations is extremely crucial to any efficient business.

The playbook implements the following tasks:

- Install Docker
- Install pip3 Module
- Add and increase the memory usage
- download and launch the ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.6
- 10.0.0.7
- 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Store system log files such as audit output. The logfile audit output is the only output for auditing. It writes data to the <clustername>_audit.json file in the logs directory.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configuration file to the web servers.
- Update the configuration file to include the IP of your ELK VM
- Run the playbook, and navigate to http://[yourip]:5601/app/kibana to check that the installation worked as expected.
