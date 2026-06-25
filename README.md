# AWS Ansible Automation

## Project Overview

This project demonstrates Infrastructure Automation using Ansible, Docker, Ansible Navigator, and GitHub on AWS EC2 instances.

The project is divided into two missions:

* **Mission 1:** Build and Configure an Ansible Environment in AWS Mumbai Region.
* **Mission 2:** Recreate the Environment in AWS Hyderabad Region by cloning the existing GitHub repository and executing all automation playbooks.

The objective is to automate package management, web server deployment, content management, and server configuration using Ansible playbooks and roles.

---

# Technologies Used

* AWS EC2
* Amazon Linux 2023
* Ansible
* Ansible Navigator
* Docker
* Apache Web Server
* MariaDB
* PHP
* Git
* GitHub
* SSH

---

# Mission 1 – Build & Configure Ansible Environment (Mumbai Region)

## Infrastructure Setup

### Control Node

* Instance Name: mumbai-control
* User: devops
* Installed Components:

  * Docker
  * Ansible
  * Ansible Navigator

### Client Nodes

#### mumbai-client1

* User: devops
* Group: dev

#### mumbai-client2

* User: devops
* Group: test

---

## Project Structure

```text
/home/devops/ansible

├── ansible.cfg
├── inventory
├── packages.yml
├── myrole.yml
├── issue.yml
├── custom.yml
└── roles
    └── myrole
        ├── tasks
        ├── templates
        ├── handlers
        └── defaults
```

---

## Task 1 – Install and Configure Ansible Environment

Completed:

* Docker Installation
* Ansible Installation
* Ansible Navigator Installation
* Inventory Configuration
* Ansible Configuration
* SSH Connectivity Verification

Command:

```bash
ansible all -m ping
```

---

## Task 2 – Package Management Automation

Playbook: `packages.yml`

### Dev Group

* Update all packages
* Install RPM Development Tools

### Test Group

* Install MariaDB Server
* Install PHP

Execution:

```bash
ansible-navigator run packages.yml -m stdout
```

---

## Task 3 – Create and Use Roles

Role Name:

```text
myrole
```

Features:

* Install Apache Web Server
* Enable Apache Service
* Start Apache Service
* Deploy Web Template

Template:

```html
Welcome to
{{ ansible_hostname }}

on

{{ ansible_default_ipv4.address }}
```

Execution:

```bash
ansible-navigator run myrole.yml -m stdout
```

---

## Task 4 – Content Modification

Playbook:

```text
issue.yml
```

Content Changes:

### Dev Group

```text
development
```

### Test Group

```text
test
```

Execution:

```bash
ansible-navigator run issue.yml -m stdout
```

---

## Task 5 – Custom-Based Web Server

Playbook:

```text
custom.yml
```

Configuration:

* Document Root: /webdev
* Symbolic Link: /var/www/html -> /webdev

Custom Content:

```html
Welcome to my page

Apache Web Server Configured Successfully
```

Execution:

```bash
ansible-navigator run custom.yml -m stdout
```

---

## Task 6 – Git Integration

Repository created and uploaded to GitHub.

Repository URL:

https://github.com/jithams/aws-ansible-automation

---

# Mission 2 – Recreate Environment in Hyderabad Region

## Infrastructure Setup

### Control Node

* Instance Name: hyderabad-control
* User: clone

### Client Nodes

#### hyderabad-client1

* User: clone
* Group: dev

#### hyderabad-client2

* User: clone
* Group: test

---

## Environment Recreation

The existing automation repository from Mission 1 was cloned into the new environment.

Clone Location:

```text
/home/clone/ansible
```

Command:

```bash
git clone https://github.com/jithams/aws-ansible-automation.git ansible
```

---

## Inventory Update

Updated inventory with:

* Hyderabad hostnames
* Hyderabad private IP addresses

Verified connectivity:

```bash
ansible all -m ping
```

---

## Playbook Execution

Successfully executed all existing playbooks:

### packages.yml

```bash
ansible-navigator run packages.yml -m stdout
```

### myrole.yml

```bash
ansible-navigator run myrole.yml -m stdout
```

### issue.yml

```bash
ansible-navigator run issue.yml -m stdout
```

### custom.yml

```bash
ansible-navigator run custom.yml -m stdout
```

---

## Validation

Successfully verified:

* Package Installation
* Apache Web Server Deployment
* Template Deployment
* Content Modification
* Custom Web Server Configuration
* SSH Connectivity
* Git Repository Cloning
* Playbook Execution Using Ansible Navigator

---

# Results

* Automated package installation using Ansible.
* Automated Apache web server deployment.
* Implemented reusable Ansible roles.
* Managed content updates using playbooks.
* Configured custom web server document roots.
* Integrated project with GitHub.
* Successfully recreated the environment in a different AWS region.
* Demonstrated Infrastructure as Code (IaC) and automation consistency.

---

# GitHub Repository

Repository URL:

https://github.com/jithams/aws-ansible-automation

---

# Author

Jitha M S

AWS EC2 Infrastructure Automation using Ansible, Docker, Roles, Templates, and Git Integration.
