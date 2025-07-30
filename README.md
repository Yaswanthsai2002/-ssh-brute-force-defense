# 🔐 SSH Brute-Force Defense on Ubuntu Server

This project simulates **SSH brute-force attacks** and showcases a layered defense strategy using **Fail2Ban** on an Ubuntu server.  
It mimics real-world threat scenarios and blue-team incident response.

---

## 🎯 Objective

To detect, prevent, and mitigate SSH brute-force login attempts using:
- Fail2Ban
- UFW Firewall
- Log Monitoring (auth.log)

---

## 🏗️ Lab Setup

| Component        | Configuration         |
|------------------|------------------------|
| OS               | Ubuntu 22.04 LTS       |
| SSH Service      | OpenSSH Server         |
| Tool Used        | Hydra (for attack simulation) |
| Defense Tool     | Fail2Ban + UFW         |

---

## ⚙️ Steps Performed

1. 📥 Installed & configured OpenSSH and Fail2Ban
2. 🔐 Created jail for SSHD with `maxretry=3`, `bantime=3600`
3. 🧪 Simulated brute-force using THC-Hydra
4. 🔍 Monitored logs using `tail -f /var/log/auth.log`
5. 🔥 Automatically banned attacker IP using Fail2Ban
6. 📊 Verified ban using `iptables -L`

---

## 🖼️ Screenshots

> Add screenshots of Hydra brute-force, Fail2Ban bans, UFW logs, and jail config

---

## 📁 Directory Structure

