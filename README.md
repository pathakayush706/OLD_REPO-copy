````md
<p align="center">
  <img src="assets/banner.svg" alt="LinuxOps Troubleshooting Lab" width="100%">
</p>

# 🛠️ LinuxOps - Production Troubleshooting Lab

[![Linux](https://img.shields.io/badge/Linux-System%20Administration-blue?style=flat-square&logo=linux)](https://www.linux.org/)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-Lab%20Server-orange?style=flat-square&logo=ubuntu)](https://ubuntu.com/)
[![Nginx](https://img.shields.io/badge/Nginx-Web%20Server-green?style=flat-square&logo=nginx)](https://nginx.org/)
[![SSH](https://img.shields.io/badge/SSH-Remote%20Access-lightgrey?style=flat-square)](#)
[![Tomcat](https://img.shields.io/badge/Tomcat-Application%20Server-yellow?style=flat-square&logo=apachetomcat)](https://tomcat.apache.org/)
[![Troubleshooting](https://img.shields.io/badge/Focus-Root%20Cause%20Analysis-purple?style=flat-square)](#)

LinuxOps is a hands-on Linux system administration lab focused on production-style troubleshooting.

This project recreates common Linux server incidents around SSH access, Nginx, DNS and hosts entries, firewall rules, log permissions, disk and memory issues, mounting with `/etc/fstab`, and Tomcat application server operations.

The goal is simple: identify the symptom, confirm the affected layer, find the root cause, apply a safe fix, and verify the result with clear before and after evidence.

---

## ✨ Highlights

- 🔐 SSH access and service troubleshooting
- 🌐 Nginx web server incident handling
- 🧭 DNS and `/etc/hosts` issue analysis
- 🔥 Firewall rule investigation
- 📜 Log file and directory permission debugging
- 💽 Disk space and memory usage troubleshooting
- 🗂️ Mounting and `/etc/fstab` recovery
- ☕ Tomcat application server troubleshooting
- 📸 Screenshot-backed before and after verification
- 🚀 Interview-ready Linux administration documentation

---

## 🧪 Completed Troubleshooting Sections

| No. | Section | Folder | What It Covers |
|---|---|---|---|
| 1 | SSH Issues | [ssh-issues](ssh-issues/) | SSH access, service, port, and configuration checks |
| 2 | Nginx Issues | [nginx-issues](nginx-issues/) | Web service access, permissions, config, and port checks |
| 3 | DNS and Hosts Issues | [dns-hosts-issues](dns-hosts-issues/) | Wrong and missing `/etc/hosts` entries |
| 4 | Firewall Issues | [firewall-issues](firewall-issues/) | HTTP and ICMP traffic blocked by firewall rules |
| 5 | Logs and Permission Issues | [logs-permission-issues](logs-permission-issues/) | Log read and write permission failures |
| 6 | Disk and Memory Issues | [disk-memory-issues](disk-memory-issues/) | Disk full and high memory usage incidents |
| 7 | Mounting and Fstab Issues | [mounting-fstab-issues](mounting-fstab-issues/) | Missing mount point and wrong filesystem type in `/etc/fstab` |
| 8 | Tomcat Troubleshooting | [tomcat-troubleshooting](tomcat-troubleshooting/) | Tomcat startup failure and port 8080 conflict |

---

## 🏗️ Troubleshooting Approach

LinuxOps follows a simple layered troubleshooting flow:

```text
Symptom → Service → Port → Config → Logs → Root Cause → Fix → Verification
```

The same approach is used across all scenarios.

### 1. Service Layer

- Check if the service or process is running
- Confirm the expected port is listening
- Restart only after understanding the failure

### 2. Network and Access Layer

- Test local access with `curl`
- Check listening ports with `ss`
- Confirm firewall rules when traffic is blocked

### 3. Configuration Layer

- Validate files like `/etc/hosts`, `/etc/fstab`, and service configs
- Keep changes small and easy to reverse
- Avoid risky commands in lab scenarios

### 4. Logs and Evidence Layer

- Use simple log checks
- Capture before and after screenshots
- Verify the fix with command output

---

## 🧰 Basic Lab Tools

Install the common tools used in the lab:

```bash
sudo apt update
sudo apt install -y nginx openssh-server curl vim git iproute2 iputils-ping iptables python3 openjdk-17-jdk wget tar
```

Verify important commands:

```bash
nginx -v
curl --version
git --version
ss -V
java -version
```

---

## 🔐 SSH Troubleshooting

SSH scenarios focus on remote access problems and service validation.

Common checks:

```bash
systemctl status ssh
ss -ltnp | grep ssh
ssh localhost
sudo tail -n 20 /var/log/auth.log
```

Skills practiced:

- SSH service validation
- Port listening checks
- Access failure investigation
- Log-based troubleshooting

---

## 🌐 Nginx Troubleshooting

Nginx scenarios focus on website access failures, port checks, service status, and configuration validation.

Common checks:

```bash
systemctl status nginx
curl -I http://localhost
ss -ltnp | grep 80
sudo nginx -t
sudo tail -n 20 /var/log/nginx/error.log
```

Skills practiced:

- Web service troubleshooting
- Nginx config validation
- Permission issue investigation
- Port and access verification

---

## 🧭 DNS and Hosts Troubleshooting

DNS and hosts scenarios use safe local test hostnames and avoid changing the real `localhost` entry.

Completed scenarios:

| Scenario | What Happened |
|---|---|
| [Wrong Hosts Entry](dns-hosts-issues/dns-wrong-hosts-entry.md) | Hostname pointed to the wrong IP address in `/etc/hosts` |
| [Missing Hosts Entry](dns-hosts-issues/dns-hosts-missing-host-entry.md) | Hostname failed because the hosts entry was missing |

Common checks:

```bash
cat /etc/hosts
curl http://127.0.0.1:8081
curl http://app.lab:8081
ss -ltnp | grep 8081
```

Skills practiced:

- Hostname resolution troubleshooting
- `/etc/hosts` validation
- Local application connectivity testing
- Simple fix and verification

---

## 🔥 Firewall Troubleshooting

Firewall scenarios focus on traffic blocked by simple firewall rules.

Completed scenarios:

| Scenario | What Happened |
|---|---|
| [HTTP Port Blocked](firewall-issues/firewall-http-port-blocked.md) | Web traffic was blocked by a firewall rule |
| [ICMP Ping Blocked](firewall-issues/firewall-icmp-ping-blocked.md) | Ping failed because ICMP traffic was blocked |

Common checks:

```bash
sudo iptables -L -n -v
curl -I http://localhost
ping 127.0.0.1
```

Skills practiced:

- Firewall rule validation
- Blocked traffic investigation
- HTTP and ICMP testing
- Rule removal and verification

---

## 📜 Logs and Permission Troubleshooting

Logs and permission scenarios focus on read and write failures caused by wrong ownership or permissions.

Completed scenarios:

| Scenario | What Happened |
|---|---|
| [Log File Permission Denied](logs-permission-issues/logs-file-permission-denied.md) | Application user could not read the log file |
| [Log Directory Write Permission Denied](logs-permission-issues/logs-directory-write-permission-denied.md) | Application user could not create or write log files |

Common checks:

```bash
ls -l /var/log/loglab/app.log
ls -ld /var/log/loglab
sudo -u loglabuser tail -n 5 /var/log/loglab/app.log
sudo -u loglabuser touch /var/log/loglab/app-new.log
```

Skills practiced:

- File permission troubleshooting
- Directory permission troubleshooting
- Ownership validation
- User-based verification

---

## 💽 Disk and Memory Troubleshooting

Disk and memory scenarios focus on common resource issues that affect application stability.

Completed scenarios:

| Scenario | What Happened |
|---|---|
| [Disk Space Full](disk-memory-issues/disk-space-full.md) | Application could not write files because the filesystem was full |
| [Memory Usage High](disk-memory-issues/memory-usage-high.md) | Server became slow because a process consumed too much memory |

Common checks:

```bash
df -h
ls -lh
free -h
ps aux --sort=-%mem | head
```

Skills practiced:

- Disk space validation
- Large file cleanup
- Memory usage analysis
- Process-level verification

---

## 🗂️ Mounting and Fstab Troubleshooting

Mounting scenarios focus on safe `/etc/fstab` issues using test mounts.

Completed scenarios:

| Scenario | What Happened |
|---|---|
| [Fstab Mount Point Missing](mounting-fstab-issues/fstab-mount-point-missing.md) | Mount failed because the mount point directory did not exist |
| [Fstab Wrong Filesystem Type](mounting-fstab-issues/fstab-wrong-filesystem-type.md) | Mount failed because `/etc/fstab` had the wrong filesystem type |

Common checks:

```bash
cat /etc/fstab
sudo mount -a
df -h
mount | grep fstab
```

Skills practiced:

- `/etc/fstab` validation
- Mount error investigation
- Filesystem type troubleshooting
- Post-fix mount verification

---

## ☕ Tomcat Troubleshooting

Tomcat scenarios use a local Tomcat installation under:

```text
/home/aayush-pathak/tomcat
```

Completed scenarios:

| Scenario | What Happened |
|---|---|
| [Tomcat Service Not Running](tomcat-troubleshooting/tomcat-service-not-running.md) | Tomcat was stopped and port 8080 was not reachable |
| [Tomcat Port Conflict](tomcat-troubleshooting/tomcat-port-conflict.md) | Tomcat failed to start because another process was using port 8080 |

Common checks:

```bash
/home/aayush-pathak/tomcat/bin/startup.sh
/home/aayush-pathak/tomcat/bin/shutdown.sh
ss -ltnp | grep 8080
curl http://127.0.0.1:8080
tail -n 20 /home/aayush-pathak/tomcat/logs/catalina.out
```

Skills practiced:

- Tomcat startup and shutdown checks
- Port 8080 validation
- Port conflict investigation
- Tomcat log verification

---

## 📸 Evidence and Screenshots

Each scenario includes before and after screenshots stored under:

```text
screenshots/<topic-name>/<scenario-name>/
```

Most scenarios include:

```text
before screenshot
root-cause screenshot
after/fixed screenshot
```

This keeps every incident easy to review on GitHub.

---

## ✅ Final Result

This project documents a practical Linux troubleshooting workflow across 8 production-style areas:

```text
SSH → Nginx → DNS/Hosts → Firewall → Logs/Permissions → Disk/Memory → Mounting/Fstab → Tomcat
```

Each section shows the issue, investigation, root cause, fix, verification, and screenshot evidence.

---

## 👨‍💻 Author

Created by **Aayush Pathak**

Linux system administration and production troubleshooting practice.
````
