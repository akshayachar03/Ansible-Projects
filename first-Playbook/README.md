# Ansible First Playbook

## Overview
This repository contains an Ansible playbook designed to automate essential tasks on remote servers. The playbook is structured to ensure efficient configuration management and deployment.

## Requirements
- Ansible installed on the control node
- SSH access to the target servers
- A valid inventory file with target server details

## Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/akshayachar03/Ansible-Projects.git
   cd Ansible-Projects/first-Playbook
   ```
2. Ensure Ansible is installed:
   ```sh
   ansible --version
   ```

## Usage
Run the playbook using the following command:
```sh
ansible-playbook -i inventory playbook.yml
```

## File Structure
```
first-Playbook/
├── inventory.ini    # Define target hosts
├── playbook.yaml    # Main Ansible playbook
├── index.html       # Main Ansible playbook
└── README.md        # Documentation
```


