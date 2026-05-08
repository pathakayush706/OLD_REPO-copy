<p align="center">
  <img src="assets/banner.svg" alt="LinuxOps Troubleshooting Lab" width="100%">
</p>

# 🛠️ LinuxOps - Production Troubleshooting Lab

[![Linux](https://img.shields.io/badge/Linux-System%20Administration-blue?style=flat-square&logo=linux)](https://www.linux.org/)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-Lab%20Server-orange?style=flat-square&logo=ubuntu)](https://ubuntu.com/)
[![Nginx](https://img.shields.io/badge/Nginx-Web%20Server-green?style=flat-square&logo=nginx)](https://nginx.org/)
[![Tomcat](https://img.shields.io/badge/Tomcat-Application%20Server-yellow?style=flat-square&logo=apachetomcat)](https://tomcat.apache.org/)
[![SSH](https://img.shields.io/badge/SSH-Remote%20Access-lightgrey?style=flat-square)]()
[![Bash](https://img.shields.io/badge/Shell-Bash-black?style=flat-square&logo=gnubash)]()

LinuxOps is a hands-on Linux system administration lab focused on production-style troubleshooting.

This project recreates common Linux server incidents around web services, SSH access, DNS, firewall rules, permissions, logs, system resources, mounting, and Tomcat application server operations.

---

## ✨ Features

- 🌐 Nginx web server troubleshooting
- 🔐 SSH remote access troubleshooting
- 🧭 DNS and `/etc/hosts` issue analysis
- 🔥 Firewall investigation using iptables
- 📁 File and directory permission debugging
- 💾 Disk, inode, and filesystem checks
- 📊 CPU, memory, swap, and disk I/O troubleshooting
- 📜 Service and system log analysis
- ☕ Tomcat application server operations
- 🧪 Root cause analysis with verification

---

## 🏗️ Architecture

LinuxOps follows a layered troubleshooting approach.

### 1. Client Layer

- Browser request
- SSH connection
- DNS lookup
- Remote access using server IP or hostname

### 2. Linux Server Layer

- Services managed by systemd
- Network interface and routing
- Firewall rules
- File permissions
- Logs and system resources

### 3. Application Layer

- Nginx web server
- Tomcat application server
- Application ports
- Runtime process state
- Application and service logs

---

## 🧰 Toolbox

### Linux / Web / Application Server

<p>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" width="48"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ubuntu/ubuntu-plain.svg" width="48"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nginx/nginx-original.svg" width="48"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/tomcat/tomcat-original.svg" width="52"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" width="52"/>
</p>

### Shell / Version Control

<p>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bash/bash-original.svg" width="48"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" width="48"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" width="48"/>
</p>

---

## PreRequisites

> [!IMPORTANT]
> Use a local VM or lab machine for these scenarios. Do not run break/fix practice directly on production servers.

Install required packages:

    sudo apt update
    sudo apt install nginx openssh-server curl vim git net-tools iproute2 iputils-ping iptables sysstat lsof -y

Verify important tools:

    nginx -v
    curl --version
    git --version
    ss -V
    iostat -V

---

## Setup & Initialization

### 1. Start Nginx

    sudo systemctl enable nginx
    sudo systemctl start nginx

### 2. Verify Nginx Service

    systemctl status nginx

### 3. Test Website Locally

    curl -I http://localhost

Expected output:

    HTTP/1.1 200 OK

### 4. Check Listening Port

    ss -tulnp | grep :80

### 5. Check Logs

    journalctl -u nginx
    tail -n 50 /var/log/nginx/error.log

---

## Troubleshooting Workflow

### Website Issue Flow

    Application → Service → Port/Bind → Network → DNS → Firewall → Logs

### SSH Issue Flow

    Service → Port → Network Reachability → Firewall → Config → Logs

### Performance Issue Flow

    CPU → Memory → Swap → Disk → Process → Logs

---

## Nginx Operations

Common Nginx incidents covered in this lab:

- Website returning `403 Forbidden`
- Nginx service running but website not accessible
- Localhost working but remote access failing
- Port 80 binding issue
- Nginx configuration error
- Nginx log investigation

Useful commands:

    curl -I http://localhost
    curl -I http://<server-ip>
    systemctl status nginx
    ss -tulnp | grep :80
    nginx -t
    nginx -T
    tail -n 50 /var/log/nginx/error.log

---

## SSH Operations

Common SSH incidents covered in this lab:

- SSH service not running
- SSH port not listening
- Firewall blocking SSH
- SSH configuration issue
- Authentication failure investigation

Useful commands:

    systemctl status ssh
    ss -tulnp | grep ssh
    ping <server-ip>
    iptables -L -n -v
    journalctl -u ssh
    grep -Ei '^(Port|ListenAddress|PermitRootLogin|PasswordAuthentication|AllowUsers|DenyUsers)' /etc/ssh/sshd_config

---

## DNS and Network Operations

Common DNS and network incidents covered in this lab:

- IP connectivity works but domain fails
- Wrong `/etc/hosts` entry
- Wrong DNS resolver configuration
- Missing route or gateway issue
- Server reachable locally but not externally

Useful commands:

    ip a
    ip route
    ping 8.8.8.8
    ping google.com
    cat /etc/hosts
    cat /etc/resolv.conf
    resolvectl status

---

## Firewall Operations

Common firewall incidents covered in this lab:

- HTTP traffic blocked
- SSH traffic blocked
- DNS traffic blocked
- INPUT and OUTPUT chain analysis
- DROP rule investigation

Useful commands:

    iptables -L -n -v
    iptables -A INPUT -p tcp --dport 80 -j DROP
    iptables -D INPUT -p tcp --dport 80 -j DROP
    iptables -A OUTPUT -p udp --dport 53 -j DROP
    iptables -D OUTPUT -p udp --dport 53 -j DROP

---

## System Resource Operations

Common system incidents covered in this lab:

- Disk full issue
- Inode full issue
- High CPU usage
- High memory usage
- Swap activity
- Disk I/O bottleneck
- OOM kill investigation

Useful commands:

    df -h
    df -i
    du -h --max-depth=1 /
    find / -type f -size +1G 2>/dev/null
    top
    free -h
    vmstat 1
    iostat -x 1
    ps aux --sort=-%mem | head
    ps -eo pid,ppid,cmd,%cpu --sort=-%cpu | head
    dmesg | grep -i kill

---

## Mounting and Filesystem Operations

Common filesystem incidents covered in this lab:

- Disk visible but not mounted
- Wrong `/etc/fstab` entry
- UUID mismatch
- Read-only filesystem issue
- Mount verification after reboot

Useful commands:

    lsblk
    blkid
    mount
    umount
    df -h
    cat /etc/fstab
    mount -a

---

## Tomcat Operations

Tomcat is included because Linux support roles commonly involve Java application server troubleshooting.

### Install Tomcat

Check available package:

    apt-cache search '^tomcat[0-9]'

Install based on OS version:

    sudo apt install tomcat9 -y

or:

    sudo apt install tomcat10 -y

### Validate Tomcat

    systemctl status tomcat9
    systemctl status tomcat10
    ss -tulnp | grep :8080
    curl -I http://localhost:8080

### Common Tomcat Incidents

- Tomcat service not running
- Port 8080 not listening
- Port conflict on 8080
- Application not opening
- WAR deployment issue
- Tomcat log investigation
- Java process high CPU or memory usage

Useful commands:

    systemctl status tomcat9
    systemctl status tomcat10
    ss -tulnp | grep :8080
    curl -I http://localhost:8080
    journalctl -u tomcat9
    journalctl -u tomcat10
    ls -l /var/log/tomcat*

---

## Lab Scenarios

### Nginx

- Nginx 403 Forbidden due to file permission
- Localhost works but remote access fails
- Port binding issue
- Configuration and log analysis

### SSH

- SSH service troubleshooting
- SSH port validation
- Firewall block investigation
- SSH configuration check

### DNS and Firewall

- IP works but domain fails
- `/etc/hosts` override issue
- DNS resolver issue
- HTTP, SSH, and DNS firewall blocks

### System Resources

- Disk full issue
- Inode full issue
- High memory usage
- Swap activity
- Disk performance issue
- OOM kill investigation

### Tomcat

- Tomcat port 8080 not accessible
- Tomcat service issue
- Tomcat application not opening
- Tomcat log troubleshooting

---

## Key Learning

Troubleshooting is not about guessing.

It is about checking the symptom, isolating the layer, reading the output, fixing the root cause, and verifying the result.

---

## Author

Created by **Aayush Pathak**

Linux system administration and production troubleshooting practice.
