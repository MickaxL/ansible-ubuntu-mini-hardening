![Ansible](https://img.shields.io/badge/Ansible-2.16+-red?logo=ansible)
![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04%2F24.04-orange?logo=ubuntu)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

# 🔒 Ansible Ubuntu Mini Hardening

Automated application of essential security controls on Ubuntu Server (tested on 22.04 / 24.04 LTS).

This project applies a safe and minimal subset of **CIS Ubuntu Linux Benchmark Level 1** controls 
using Ansible — without breaking core functionality.

> 💼 Inspired by my final internship at **Quite Good (Luxembourg)** where I worked as a 
> Cyber Security Engineer, automating server hardening and access management across 
> multi-distro environments.

---

## 🎯 Goal

Quickly secure Ubuntu servers while building toward a **multi-distro hardening framework** 
(Ubuntu, Debian, Rocky/AlmaLinux, etc.).

---

## 📁 Project Structure
```
ansible-ubuntu-mini-hardening/
├── hardening.yml          # Main playbook
├── inventory.ini          # Target hosts
└── roles/
    ├── update-system/     # System updates & auto-patches
    ├── ssh-hardening/     # SSH lockdown
    ├── perm-hardening/    # Critical file permissions
    ├── disable_ipv6/      # Disable IPv6
    └── useless-services/  # Remove dangerous services
```

---

## 🛡️ Current Roles & Controls

### `update-system`
- Full system update & upgrade
- Enable unattended-upgrades for automatic security patches

### `ssh-hardening`
- Disable root login via SSH
- Disable password authentication (force key-based only)

### `perm-hardening`
- Strict permissions on critical files
  - `/etc/passwd` → 644
  - `/etc/shadow` → 600
  - `/etc/sshd_config` → 600

### `disable_ipv6`
- Disable IPv6 if not required (reduces attack surface)

### `useless-services`
- Disable dangerous/unused services (telnet, rsh, xinetd, etc.)

---

## 🚀 Usage

### 1. Clone the repo
```bash
git clone https://github.com/MickaxL/ansible-ubuntu-mini-hardening.git
cd ansible-ubuntu-mini-hardening
```

### 2. Edit your inventory
```ini
[ubuntu]
192.168.1.100 ansible_user=youruser
```

### 3. Dry-run first (recommended ✅)
```bash
ansible-playbook -i inventory.ini hardening.yml --check --diff
```

### 4. Apply hardening
```bash
ansible-playbook -i inventory.ini hardening.yml
```

---

## ✅ Tested On

| OS | Version | Ansible | Python |
|----|---------|---------|--------|
| Ubuntu Server | 24.04 LTS | 2.16+ | 3.10+ |
| Ubuntu Server | 22.04 LTS | 2.16+ | 3.10+ |

---

## 🔜 Roadmap

- [x] SSH hardening
- [x] File permissions
- [x] Disable unused services
- [x] Auto-updates
- [ ] UFW firewall rules
- [ ] fail2ban integration
- [ ] auditd basic configuration
- [ ] Compliance report output (JSON/HTML)
- [ ] Multi-distro support

---

## 📚 References

- [CIS Ubuntu Linux Benchmark](https://www.cisecurity.org/benchmark/ubuntu_linux)
- [Ansible Documentation](https://docs.ansible.com/)

---

## 👤 Author

**Mickaël Paquet** — Junior Cybersecurity Engineer  
[LinkedIn](https://www.linkedin.com/in/mickael-paquet7a0638312) · 
[GitHub](https://github.com/MickaxL)