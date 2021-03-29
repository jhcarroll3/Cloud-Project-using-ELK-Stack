# Project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Cloud Diagram](https://github.com/jhcarroll3/Project-1/blob/main/Diagrams/Cloud%20Diagram.png)
        
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the [YAML](https://en.wikipedia.org/wiki/YAML) file may be used to install only certain pieces of it, such as Filebeat.

  - 
    
    *Step 1:*
    
    [ansible-config](https://github.com/jhcarroll3/Project-1/blob/main/Ansible/ansible-config.yml)
    
    *Step 2:*
    
    [install-elk.yml](https://github.com/jhcarroll3/Project-1/blob/main/Ansible/install-elk.yml)
    
    *Step 3:*
    
    [filebeat_config](https://github.com/jhcarroll3/Project-1/blob/main/Ansible/filebeat-configuration.yml)
    
    [filebeat-playbook.yml](https://github.com/jhcarroll3/Project-1/blob/main/Ansible/filebeat-playbook.yml)
     
    *Step 4:*
    
    [metricbeat-config](https://github.com/jhcarroll3/Project-1/blob/main/Ansible/metricbeat-configuration.yml)
    
    [metricbeat-playbook.yml](https://github.com/jhcarroll3/Project-1/blob/main/Ansible/metricbeat-playbook.yml)
    
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
- Load balancers ensure no single server has too much traffic to handle. They help protect the availability of resources. Jump Boxes are typically used for a system tool that needs to connect directly to the devices on the security zone in question.  The hidden benefit of using a Jump Box is that any tools in place are maintained on the single system of the Jump Box itself. Any updates that need to occur by a system's software are managed by the Jump Box alone. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the metrics and system logs.
- Filebeat watches and monitors the log files or locations that users specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing. 
- Metricbeat collects and ships various system and service metrics to a specified output destination. Metricbeat is installed on the different servers in your environment and used for monitoring their performance, as well as that of different external services running on them.

The configuration details of each machine may be found below.

| Name      | Function | IP Address | Operating System |
|-----------|----------|------------|------------------|
| Jump Box  | Gateway  | 10.0.0.4   | Linux            |
| ELK-SERVER| Monitor  | 10.1.0.4   | Linux            |
|   Web-1   | Website  | 10.0.0.5   | Linux            |
|   Web-2   | Website  | 10.0.0.6   | Linux            |
|   Web-3   | Website  | 10.0.0.7   | Linux            | 

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the *Workstation* machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- [REDACTED] *Host Public IP*

Machines within the network can only be accessed by *ssh*.
- *Jump Box*   *Private IP*:*10.0.0.4*
               *Public IP* :*104.214.77.211 

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses |
|-----------|---------------------|----------------------|
| Jump Box  |     No              |   Host Public IP     |
| ELK-SERVER|     No              |   Host Public IP     |
|   Web-1   |     No              |   Host Public IP     |
|   Web-2   |     No              |   Host Public IP     |
|   Web-3   |     No              |   Host Public IP     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_The advantage of automated configuration with Ansible is that it increases efficiency when configuring multiple machines.

The playbook implements the following tasks:
- 
- 1. Install docker.io - *to update the cache*
- 2. Install pip3 and python
- 3. Increase virtual memory
- 4. Download and launch a docker *elk* container     
- 5. Enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[docker ps output](https://github.com/jhcarroll3/Project-1/blob/main/Diagrams/sudo%20docker%20ps_screenshot.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 
  - _Web-1_: *10.0.0.5*
  - _Web-2_: *10.0.0.6*
  - _Web-3_: *10.0.0.7*

We have installed the following Beats on these machines:
  - *Filebeat*
  - *Metricbeat*

These Beats allow us to collect the following information from each machine:
- 
  - *Filebeat* collects log events, and forwards the information to *Elasticsearch* or *Logstash* for indexing.
  - *Metricbeat* collects system metrics from the operating system as well as system services. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- _Which file is the playbook? *Answer:* [install-elk.yml] Copy this playbook to the__ *Answer:* /etc/ansible folder.
- _Which file do you update to make Ansible run the playbook on a specific machine? Answer: Update the [ansible-config].  How do I specify which machine to install the ELK server on versus which to install Filebeat on?_*Answer:* First, update the hostname in the hosts file and then save. Next, update the [ansible-config] file and then save.
- _Which URL do you navigate to in order to check that the ELK server is running? *Answer*: Enter: http://[ELK-SERVER Public IP]:5601

_ Commands you need to know:                                                               
  *Download:* ansible-playbook name-of-file.yml
  *Updating the files:* nano name-and-path-of-file.yml
