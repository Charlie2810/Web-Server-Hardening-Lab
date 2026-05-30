# Web Server Hardening Lab

## 🛡️ Overview
This project demonstrates how to install and configure an Apache web server on **Kali Linux**, perform vulnerability scanning, and apply hardening measures. It combines offensive security techniques for discovery with defensive actions to reduce risk.

## Objectives
- Install and enable a basic Apache2 web server.
- Scan the web service using **Nmap** and **Nikto**.
- Identify and remediate common Apache security issues.
- Document findings before and after hardening.

## Tools
- **Apache2** – Web server software.
- **Nmap** – Port and service discovery.
- **Nikto** – Web application vulnerability scanner.

## Prerequisites
- Kali Linux or Debian-based Linux environment.
- Root or sudo privileges.
- Internet access to install packages and updates.

## Setup Instructions
1. Update package sources:
   ```bash
   sudo apt update
   ```
2. Install Apache2:
   ```bash
   sudo apt install apache2 -y
   ```
3. Start and enable the Apache service:
   ```bash
   sudo systemctl start apache2
   sudo systemctl enable apache2
   ```
4. Verify the server is running:
   ```bash
   sudo systemctl status apache2
   ```
5. Open a browser and visit:
   ```
   http://localhost
   ```

## Scanning and Assessment
### Nmap Scan
Run a service scan on the local host:
```bash
sudo nmap -sV localhost
```
Expected findings:
- Port 80 open for Apache HTTP.
- Port 22 open for SSH (if enabled).

### Nikto Scan
Run Nikto against the web server:
```bash
sudo nikto -h http://localhost
```
Common findings include:
- Outdated Apache version information.
- Directory listing enabled.
- Missing security headers.

## Hardening Steps
### Disable directory listing
Edit the Apache configuration or `.htaccess` file and add:
```apache
Options -Indexes
```
Then restart Apache:
```bash
sudo systemctl restart apache2
```

### Update Apache
Upgrade the installed Apache package:
```bash
sudo apt upgrade apache2 -y
```
Restart the service again after updates:
```bash
sudo systemctl restart apache2
```

### Add security headers
Consider adding the following headers in your Apache config or virtual host:
```apache
Header always set X-Frame-Options "DENY"
Header always set X-Content-Type-Options "nosniff"
Header always set Referrer-Policy "no-referrer"
```

## Results
### Before Hardening
- Apache reported as outdated.
- Directory listing was enabled.
- Security headers were missing.

### After Hardening
- Apache updated to the latest version available.
- Directory listing disabled.
- Web server security posture improved.

## Suggested Improvements
- Configure HTTPS with SSL/TLS certificates.
- Enable HTTP Strict Transport Security (HSTS).
- Regularly install security updates.
- Add a web application firewall (WAF) for additional protection.

## Notes
This repository is intended as a lab exercise for learning web server hardening techniques on Kali Linux. Use it as a foundation for further security testing and configuration.
