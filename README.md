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
```

### 📁 Step 2: Extract Attempted Usernames
```bash
cat /var/log/secure | grep "Failed password" | awk '{print $9}' | sort | uniq -c
```

### 📁 Step 3: Match Against Valid Users
```bash
awk -F: '{print $1}' /etc/passwd > valid_users.txt
grep -F -f valid_users.txt attempted_users.txt
```

---

## 🔒 Implementing Security Enhancements

### ⚙️ Step 4: Change SSH Port
Edit:
```bash
sudo nano /etc/ssh/sshd_config
# Change to
Port 2222
sudo systemctl restart sshd
```

### 🔐 Step 5: Enforce Strong Password Policies
```bash
sudo yum install libpwquality
sudo nano /etc/security/pwquality.conf
# Add:
minlen = 12
dcredit = -1
ucredit = -1
ocredit = -1
```

### 🛡️ Step 6: Enable Fail2Ban
```bash
sudo yum install epel-release
sudo yum install fail2ban
sudo nano /etc/fail2ban/jail.local
# Add:
[sshd]
enabled = true
maxretry = 3
bantime = 600

sudo systemctl restart fail2ban
```

### 🔑 Step 7: Implement Multifactor Authentication (MFA)
```bash
sudo yum install google-authenticator
# Follow prompts to set up MFA for SSH
```

### 📈 Step 8: Continuous Monitoring
Install Nagios or Zabbix:
```bash
sudo yum install nagios
sudo systemctl start nagios
```

---

## 📸 Screenshots

> Add screenshots of:
- Brute force logs
- MFA prompt
- Fail2Ban banning IPs
- SSH config
- Monitoring dashboard (Nagios/Zabbix)

---

## 📂 Project Structure

```
centos-brute-force-defense/
├── scripts/
│   ├── extract_users.sh
│   ├── fail2ban_setup.sh
│   └── password_policy.sh
├── screenshots/
├── reports/
│   └── summary.md
└── README.md
```

---

## 🧾 Submission Checklist

- ✅ Source code (Bash scripts)
- ✅ User validation logic
- ✅ Configuration files
- ✅ Screenshots of all key steps

---

## 🧠 Conclusion

This project shows how to:
- Analyze logs & correlate login attempts
- Detect real-time threats
- Harden CentOS against brute force
- Use industry tools like **Fail2Ban**, **MFA**, **Nagios**

A strong red-team simulation with blue-team countermeasures 💥🛡️

---

## 📚 References

- [Fail2Ban Docs](https://www.fail2ban.org/)
- [Google Authenticator Setup](https://github.com/google/google-authenticator)
- [RHEL/CentOS Security Guide](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/)
