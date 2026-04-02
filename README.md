# Ansible Jenkins POC

## Structure

- `hosts.ini` - Inventory of target servers
- `deploy.yml` - Ansible playbook to update apt cache
- `Jenkinsfile` - Pipeline to run the playbook
- `README.md` - This file

## Usage

1. Add Jenkins SSH credential (`ansible-server-key`) for Ansible server
2. Ensure Ansible server can SSH to worker nodes with `ansible_ssh_private_key_file`
3. Run Jenkins job to execute playbook
