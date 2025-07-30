# 🚨 Brute Force Attack: Security Assessment & Response on CentOS VM

This project simulates a **real-world brute force attack** on a CentOS VM and walks through a step-by-step **incident response** and **hardening strategy** to prevent future attacks. It includes log analysis, user verification, SSH hardening, Fail2Ban setup, MFA, and continuous monitoring.

---

## 🎯 Objective

- Detect unauthorized SSH login attempts.
- Analyze logs and identify targeted usernames.
- Implement hardened configurations and active defenses.
- Set up real-time monitoring to track future incidents.

---

## 📋 Prerequisites

- ✅ Linux System Administration (CentOS/RHEL)
- ✅ Bash Scripting & Log Analysis
- ✅ Basic Networking & Security
- ✅ Incident Response Concepts

---

## 🔍 Log Analysis & User Verification

### 📁 Step 1: View Authentication Logs
```bash
sudo grep "Failed password" /var/log/secure
