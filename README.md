# kubernetes
# homelab MAGI project: 3-Node High-Availability k3s Cluster

This repository contains the Infrastructure as Code (IaC) for my home lab Kubernetes cluster, running on **Proxmox VE** and managed by **Ansible**.

## Architecture
The cluster consists of three virtualized nodes configured for High Availability (HA) using an embedded `etcd` datastore.


|Node Name	Role	Host OS (Physical)	Guest OS (VM)	IP Address
magi01	Master	Proxmox VE 8.x	Ubuntu 22.04	xxx.xxx.xxx.xxx
magi02	Master	Proxmox VE 8.x	Ubuntu 22.04	xxx.xxx.xxx.xxx
magi03	Master	Proxmox VE 8.x	Ubuntu 22.04	xxx.xxx.xxx.xxx

## 🛠️ Technology Stack
*   **Hypervisor**: [Proxmox VE](https://www.proxmox.com)
*   **Kubernetes Distro**: [k3s](https://k3s.io) (Lightweight K8s)
*   **Automation**: [Ansible](https://www.ansible.com) (Deployed from Fedora Workstation)
*   **Storage (Planned)**: Longhorn Distributed Block Storage

## 🚀 Deployment Steps
1. **Hardware Prep**: Configured Proxmox nodes for automatic AC Power Recovery in BIOS.
2. **Provisioning**: Created 3 VMs with static IPs and passwordless sudo/SSH.
3. **Automation**:
   ```bash
   ansible-playbook -i ansible/hosts.yml playbooks/site.yml --ask-become-pass
