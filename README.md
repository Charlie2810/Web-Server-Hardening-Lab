# Web-Server-Hardening-Lab
# 🛡️ Web Server Hardening Lab (Kali Linux)

##  Project Overview
This project demonstrates how to set up a simple web server in **Kali Linux**, scan it for vulnerabilities, and apply security fixes.  
It highlights both **offensive security (scanning)** and **defensive security (hardening)** skills.

---

##  Objectives
- Install and configure a basic Apache web server.  
- Perform vulnerability scanning using **Nmap** and **Nikto**.  
- Apply security fixes to reduce risks.  
- Document before‑and‑after results.  

---

##  Tools Used
- **Apache2** → Web server setup.  
- **Nmap** → Port and service scanning.  
- **Nikto** → Web vulnerability scanning.  

---

##  Steps Performed
1. **Web Server Setup**  
   
   sudo apt install apache2 -y
   sudo systemctl start apache2
   sudo systemctl enable apache2
→ Apache server running at http://localhost.

Initial Scanning


sudo nmap -sV localhost
sudo nikto -h http://localhost
→ Identified open ports and vulnerabilities.

Security Fixes Applied

Disabled directory listing:


Options -Indexes
Updated Apache to latest version.

Restarted server:


sudo systemctl restart apache2
Re‑Scan  
→ Confirmed vulnerabilities reduced after fixes.

# Findings
Before Fixes: Outdated Apache version, directory listing enabled, missing security headers.

After Fixes: Updated Apache, directory listing disabled, improved security posture.

# Suggested Improvements
Use HTTPS with SSL/TLS certificates.

Add security headers (X‑Frame‑Options, X‑Content‑Type‑Options).

Regular patching and monitoring.

# About Report
Web Server Hardening Lab Report

## 🛡️ Project Summary
This report documents the setup of a web server in **Kali Linux**, the vulnerabilities discovered through scanning, and the security fixes applied to harden the server.

---

## 🔹 Web Server Setup
**Command:**
```bash
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
Result:

Apache server running at http://localhost (or Kali IP).

Default Apache test page accessible.

🔹 Initial Scanning
Nmap Scan:

bash
sudo nmap -sV localhost
Findings:

Port 22 → SSH service running.

Port 80 → Apache HTTP server detected.

Nikto Scan:

bash
sudo nikto -h http://localhost
Findings:

Outdated Apache version.

Directory listing enabled.

Missing security headers.

🔹 Security Fixes Applied
Disabled directory listing in Apache config:

bash
Options -Indexes
Updated Apache to latest version:

bash
sudo apt upgrade apache2
Restarted server:

bash
sudo systemctl restart apache2
🔹 Re‑Scan Results
Directory listing disabled.

Apache updated to latest version.

Reduced vulnerabilities reported by Nikto.
📌 Outcome
This project shows how to set up a web server hardening lab in Kali Linux, perform vulnerability scanning, and apply fixes.

#Conclusion ----------------------------------------------------------------------------------------------------------------

This project demonstrates how to set up a web server hardening lab in Kali Linux, perform vulnerability scanning, and apply fixes.
It highlights practical skills in both offensive scanning and defensive hardening.
