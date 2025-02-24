# 🚀 Ansible Realtime Project: Automating EC2 Instance Management

## 📌 Project Overview
This project demonstrates how to use **Ansible** to automate the provisioning and management of **AWS EC2 instances**. The key tasks include:
- Creating EC2 instances using **Ansible loops**.
- Configuring **passwordless SSH authentication** between the Ansible control node and EC2 instances.
- Automating the **shutdown of Ubuntu instances** using Ansible conditionals.

---

## 🛠 Prerequisites
Before running the Ansible playbooks, ensure that you have the following set up:

### 1️⃣ Install Required Python Packages
```bash
pip install boto3
```

### 2️⃣ Install AWS Ansible Collection
```bash
ansible-galaxy collection install amazon.aws
```

### 3️⃣ Configure AWS Authentication using Ansible Vault
Generate a **vault password file**:
```bash
openssl rand -base64 2048 > vault.pass
```

Securely store your **AWS credentials** in an encrypted file:
```bash
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
```

---

## 🚀 Task 1: Creating EC2 Instances Using Ansible
The `ec2_create.yaml` playbook provisions three EC2 instances:
- **2 Ubuntu Instances**
- **1 CentOS Instance**

Run the playbook using:
```bash
ansible-playbook ec2_create.yaml --vault-password-file vault.pass
```

**📌 Key Features:**
- Uses **loops** to create multiple instances.
- Uses **connection: local** to execute API calls from the Ansible control node.

---

## 🔐 Task 2: Setting Up Passwordless Authentication
After launching the EC2 instances, configure **passwordless authentication** by copying the public key to each instance:

```bash
ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>
```

This allows Ansible to connect to the instances without needing a password.

---

## 🛑 Task 3: Automating the Shutdown of Ubuntu Instances
The `ec2_stop.yaml` playbook shuts down **only the Ubuntu instances** by using **Ansible conditionals** based on gathered facts.

Run the playbook using:
```bash
ansible-playbook -i inventory.ini ec2_stop.yaml --vault-password-file vault.pass
```

**📌 Key Features:**
- Uses **`when` condition** to check if the instance is running **Ubuntu** before shutting it down.

---

## 📂 Project Structure
```
📁 Ansible-Projects
├── 📂 Resource-Creation
│   ├── ec2_create.yaml
│   ├── ec2_stop.yaml
│   ├── group_vars/all/pass.yml
│   ├── inventory.ini
│   ├── vault.pass
```

---

## 🎯 Key Takeaways
✅ **Automates EC2 provisioning** using Ansible loops.  
✅ **Ensures secure authentication** with Ansible Vault.  
✅ **Implements conditional automation** to selectively shut down Ubuntu instances.  

---

Happy Automating! 🚀

