# Homelab Project MAGI: 3-Node High-Availability k3s Cluster
![Kubernetes](https://img.shields.io) ![Ansible](https://img.shields.io) ![Proxmox](https://img.shields.io)

This repository contains the **Infrastructure as Code (IaC)** for my high-availability home lab Kubernetes cluster, virtualized on **Proxmox VE** and orchestrated via **Ansible**.

---

## Architecture
The cluster is designed for resilience using an embedded `etcd` datastore across three master nodes.


| Node Name | Role | Host OS (Physical) | Guest OS (VM) | IP Address |
| :--- | :--- | :--- | :--- | :--- |
| **magi01** | `control-plane` | Proxmox VE 8.x | Ubuntu 22.04 | `xxx.xxx.xxx.xxx` |
| **magi02** | `control-plane` | Proxmox VE 8.x | Ubuntu 22.04 | `xxx.xxx.xxx.xxx` |
| **magi03** | `control-plane` | Proxmox VE 8.x | Ubuntu 22.04 | `xxx.xxx.xxx.xxx` |

## Technology Stack
*   **Hypervisor**: [Proxmox VE](https://www.proxmox.com) — Type-1 Hypervisor.
*   **K8s Distro**: [k3s](https://k3s.io) — Lightweight, production-ready Kubernetes.
*   **Automation**: [Ansible](https://www.ansible.com) — Deployed from a Fedora workstation.
*   **Storage**: [Longhorn](https://longhorn.io) (Planned) — Distributed block storage for persistent volumes.

## Deployment Workflow

### 1. Hardware & Virtualization
*   **AC Recovery**: Enabled "Restore on AC Power Loss" in BIOS for all physical nodes.
*   **Provisioning**: Deployed 3 Ubuntu Server VMs with Cloud-Init and static IPs.
*   **Security**: Established passwordless SSH keys and `NOPASSWD` sudoers access.

### 2. Automated Installation
The cluster was initialized using the `k3s-ansible` playbook to automate the HA handshake and API endpoint configuration.


### Run the deployment from the Fedora control node
ansible-playbook -i ansible/hosts.yml playbooks/site.yml --ask-become-pass

