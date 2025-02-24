# Ansible Docker Setup using Galaxy Role

This project uses Ansible to install and configure Docker on remote EC2 instances using the `bsmeding.docker` role from Ansible Galaxy.

## Prerequisites
- Ansible installed on your local machine.
- Ansible Galaxy installed (`ansible-galaxy` command available).
- SSH access to target EC2 instances.
- A configured `inventory.ini` file with target host details.

## Installation
1. **Download the required Ansible role:**
   ```bash
   ansible-galaxy role install bsmeding.docker
   ```

2. **Create a playbook (`docker-playbook.yaml`)** that applies the role:
   ```yaml
   - hosts: all
     become: true
     roles:
       - bsmeding.docker
   ```

3. **Define the inventory (`inventory.ini`)** with target hosts:
   ```ini
   [all]
   ubuntu@174.129.58.190
   ubuntu@34.228.141.67
   ```

## Usage
Run the Ansible playbook to install Docker on the specified instances:
```bash
ansible-playbook -i inventory.ini docker-playbook.yaml
```

## Expected Output
- Docker is installed and configured on target instances.
- The user is added to the `docker` group.
- The service is started and enabled on boot.

## Verification
After execution, SSH into the target instance and run:
```bash
docker --version
```
This should return the installed Docker version.

## Conclusion
This playbook simplifies the installation and setup of Docker using a predefined Ansible Galaxy role, ensuring a consistent deployment across multiple servers.


