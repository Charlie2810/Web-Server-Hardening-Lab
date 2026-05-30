# Web-Server-Hardening-Lab


## 🛡️ Overview
This project demonstrates how to set up a simple Apache web server on **Kali Linux**, perform vulnerability scanning, and apply hardening steps to reduce risk.

The lab emphasizes:
- **Offensive security**: scanning the server with `nmap` and `nikto`
- **Defensive security**: locking down Apache and improving configuration

---

## 🚀 Objectives
- Install and configure Apache on Kali Linux
- Scan the server using `nmap` and `nikto`
- Identify and document security issues
- Apply hardening steps to lower exposure
- Verify improvements after remediation

---

## 🧰 Tools Used
- `apache2` — web server software
- `nmap` — network and service discovery
- `nikto` — web server vulnerability scanner

---

## 📌 Lab Steps
### 1. Install and start Apache
```bash
sudo apt update
sudo apt install apache2 -y
sudo systemctl enable apache2
sudo systemctl start apache2
```
Result: Apache should be running at `http://localhost` or the host IP.

### 2. Perform initial scans
```bash
sudo nmap -sV localhost
sudo nikto -h http://localhost
```
Expected findings:
- open ports such as `80` and `22`
- Apache service version
- exposed web server details
- missing security headers
- directory listing enabled

### 3. Apply security hardening
Common hardening actions:
- disable directory listing
- update Apache to the latest available version
- add security headers

Example Apache configuration change:
```apache
<Directory /var/www/html>
    Options -Indexes
</Directory>
```
Reload Apache:
```bash
sudo systemctl restart apache2
```

### 4. Re-scan and verify
```bash
sudo nmap -sV localhost
sudo nikto -h http://localhost
```
Check that:
- directory listing is disabled
- Apache is updated
- vulnerability findings are reduced

---

## 📈 Findings
### Before fixes
- outdated Apache version
- directory listing enabled
- missing security headers

### After fixes
- Apache updated
- directory listing disabled
- security posture improved

---

## 💡 Suggested Improvements
- Enable HTTPS with SSL/TLS certificates
- Add security headers such as:
  - `X-Frame-Options`
  - `X-Content-Type-Options`
  - `Referrer-Policy`
  - `Content-Security-Policy`
- Regularly patch and monitor the server
- Restrict access to management interfaces

---

## 📝 Summary
This lab shows how to build a basic Kali Linux web server hardening workflow: install Apache, identify weaknesses with scanning tools, apply configuration fixes, and confirm the server is more secure.
