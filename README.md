# 🛠️ Linux Production Troubleshooting Lab

![Linux](https://img.shields.io/badge/Linux-System%20Administration-blue)
![Nginx](https://img.shields.io/badge/Nginx-Web%20Server-green)
![Tomcat](https://img.shields.io/badge/Tomcat-Application%20Server-orange)
![SSH](https://img.shields.io/badge/SSH-Remote%20Access-yellow)
![Firewall](https://img.shields.io/badge/Firewall-iptables-red)
![Shell](https://img.shields.io/badge/Shell-Bash-black)

Linux Production Troubleshooting Lab is a hands-on Linux system administration project where I created and fixed real production-style issues in a lab environment.

This project covers troubleshooting around Nginx, SSH, DNS, firewall, permissions, logs, system resources, and Tomcat application server issues.

---

## ✨ What This Project Covers

- Nginx website troubleshooting
- SSH service and remote access troubleshooting
- DNS and `/etc/hosts` debugging
- Firewall troubleshooting using iptables
- Linux file and directory permission issues
- Disk, memory, CPU, and swap troubleshooting
- Log analysis using journalctl and application logs
- Tomcat application server troubleshooting
- Root cause analysis and verification after fix

---

## 🏗️ Troubleshooting Flow

This project follows a simple Linux troubleshooting flow:

```text
Application → Service → Port/Bind → Network → DNS → Firewall → Logs
```

For each issue, I follow this format:

```text
Issue:
What was broken?

Symptoms:
What error was observed?

Commands Used:
Commands used during troubleshooting.

Observation:
What was found from command output?

Root Cause:
Actual reason for the issue.

Fix:
What was changed to resolve it?

Verification:
How the fix was confirmed.
```

---

## ✅ Prerequisites

Before starting this lab, the following tools should be installed on the Linux machine:

- Ubuntu/Linux VM
- Nginx
- OpenSSH Server
- curl
- vim
- git
- iproute2
- iptables
- sysstat

> [!IMPORTANT]
> This project is created in a local Linux lab environment.  
> Do not run these break/fix scenarios directly on production servers.

---

## ⚙️ Setup & Initialization

### 1. Update System Packages

```bash
sudo apt update
```

### 2. Install Required Tools

```bash
sudo apt install nginx openssh-server curl vim git net-tools iproute2 iputils-ping iptables sysstat -y
```

### 3. Start and Enable Nginx

```bash
sudo systemctl enable nginx
sudo systemctl start nginx
```

### 4. Verify Nginx

```bash
systemctl status nginx
curl -I http://localhost
```

Expected output:

```text
HTTP/1.1 200 OK
```

### 5. Verify Important Tools

```bash
nginx -v
curl --version
git --version
ss -V
iostat -V
```

---

## ☕ Tomcat Setup

Tomcat is included because Linux support and system administration roles often involve Java application server troubleshooting.

### 1. Check Available Tomcat Package

```bash
apt-cache search '^tomcat[0-9]'
```

### 2. Install Tomcat

For Ubuntu versions where Tomcat 9 is available:

```bash
sudo apt install tomcat9 -y
```

For newer Ubuntu versions:

```bash
sudo apt install tomcat10 -y
```

### 3. Check Tomcat Service

```bash
systemctl status tomcat9
systemctl status tomcat10
```

### 4. Check Tomcat Port

```bash
ss -tulnp | grep :8080
```

### 5. Test Tomcat Locally

```bash
curl -I http://localhost:8080
```

---

## 📂 Project Structure

```text
linux-production-troubleshooting-lab/
├── assets/
├── docs/
├── nginx-issues/
├── ssh-issues/
├── dns-hosts-issues/
├── firewall-issues/
├── disk-memory-issues/
├── mounting-fstab-issues/
├── logs-permission-issues/
├── tomcat-troubleshooting/
└── screenshots/
```

---

## 🧪 Troubleshooting Scenarios

| No. | Scenario | Status |
|---|---|---|
| 01 | Nginx 403 Forbidden Due To File Permission | Completed |
| 02 | Nginx Works Locally But Not From Remote Machine | In Progress |
| 03 | SSH Connection Failure | Planned |
| 04 | DNS Resolution Issue | Planned |
| 05 | Firewall Blocking Traffic | Planned |
| 06 | Tomcat Port 8080 Not Accessible | Planned |
| 07 | Tomcat Service Running But Application Not Opening | Planned |

---

## 🔍 Sample Scenario: Nginx 403 Forbidden

### Issue

Website was returning `403 Forbidden`.

### Commands Used

```bash
curl -I http://localhost
systemctl status nginx
ss -tulnp | grep :80
ls -l /var/www/html/index.html
tail -n 50 /var/log/nginx/error.log
```

### Root Cause

The `index.html` file did not have read permission, so Nginx could not serve the file.

### Fix

```bash
sudo chmod 644 /var/www/html/index.html
```

### Verification

```bash
curl -I http://localhost
```

Expected output:

```text
HTTP/1.1 200 OK
```

---

## 🖼️ Screenshots

Screenshots will be added for each troubleshooting scenario.

Example structure:

```text
screenshots/nginx-403/
├── 01-error-403.png
├── 02-permission-check.png
└── 03-fixed-200-ok.png
```

---

## 🧠 Key Learning

Troubleshooting is not about guessing.

It is about checking one layer at a time, understanding the command output, finding the root cause, applying the fix, and verifying the result.

---

## 👤 Author

Created by **Aayush Pathak**

This project is part of my Linux system administration and troubleshooting practice.
