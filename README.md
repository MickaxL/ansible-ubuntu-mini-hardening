# Ansible Ubuntu Mini Hardening

Automated application of essential security controls on Ubuntu Server (tested on 22.04 / 24.04 LTS).

This project applies a safe and minimal subset of **CIS Ubuntu Linux Benchmark Level 1** controls using Ansible — without breaking core functionality.

**Goal**  
Quickly secure my homelab Ubuntu servers while building toward a **multi-distro hardening framework** (Ubuntu, Debian, Rocky/AlmaLinux, etc.), inspired by my internship on system hardening and security automation.

### Current Roles & Controls

- **update-system**  
  - Full system update & upgrade  
  - Enable unattended-upgrades for security patches  

- **ssh-hardening**  
  - Disable root login via SSH  
  - Disable password authentication (force key-based)  


- **perm-hardening**  
  - Strict permissions on critical files (/etc/passwd 644, /etc/shadow 600, sshd_config 600, etc.)  

- **disable_ipv6**  
  - Disable IPv6 if not required  

- **useless-services**  
  - Disable dangerous/unused services (telnet, rsh, xinetd, etc.)  

Planned roles: fail2ban, auditd basic, UFW firewall, reporting.

### Usage

1. Clone the repo:
   ```bash
   git clone https://github.com/MickaxL/ansible-ubuntu-mini-hardening.git
   cd ansible-ubuntu-mini-hardening

2. Edit inventory.ini
   ```bash
    [ubuntu]
    192.168.160.129 ansible_user=user  

3. Dry-run (check mode)
    ```bash
    ansible-playbook -i inventory.ini hardening.yml --check --diff

4. Apply hardening (use with caution!):
     ```bash
    ansible-playbook -i inventory.ini hardening.yml

Tested on

Ubuntu Server 24.04 LTS (VMware)
Ansible 2.16+ / Python 3.10+