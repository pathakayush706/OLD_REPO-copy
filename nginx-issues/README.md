# 🌐 Nginx Troubleshooting Scenarios

[![Linux](https://img.shields.io/badge/Linux-Server%20Administration-orange?style=flat-square&logo=linux)](https://www.linux.org/)
[![Nginx](https://img.shields.io/badge/Nginx-Web%20Server-009639?style=flat-square&logo=nginx)](https://nginx.org/)
[![Systemd](https://img.shields.io/badge/Systemd-Service%20Recovery-blue?style=flat-square&logo=linux)](#)
[![Troubleshooting](https://img.shields.io/badge/Focus-Root%20Cause%20Analysis-purple?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Scenarios-2%20Production%20Cases-success?style=flat-square)](#)

Nginx Troubleshooting Scenarios is a production-style Linux administration section focused on real web server failures, structured investigation, root-cause analysis, and safe recovery.  
It demonstrates practical troubleshooting skills using Nginx, systemd, Linux permissions, configuration validation, logs, and HTTP verification.

## ✨ Highlights

- 🔍 Realistic Nginx failure scenarios
- 🧠 Root-cause focused investigation
- 🛠️ Linux service and configuration debugging
- 🔐 File permission and web root troubleshooting
- ✅ Safe validation before reload or restart
- 📸 Screenshot-backed incident evidence
- 🚀 Interview-ready Linux administration documentation

## 🚨 Troubleshooting Scenarios

| Incident | Scenario | Focus Area |
|---|---|---|
| [Nginx 403 Forbidden - File Permission](nginx-403-forbidden-file-permission.md) | Nginx is running, but the website returns `403 Forbidden` because the index file is not readable by the web server | Permissions, ownership, web root access |
| [Nginx Configuration Syntax Error](nginx-configuration-syntax-error.md) | Nginx was running, but a wrong configuration change caused `nginx -t` and service reload to fail | Config validation, syntax troubleshooting, safe reload |

## 🏗️ Troubleshooting Coverage

This section covers the main layers involved in Nginx incident handling:

### 1. Service Layer

- Nginx service status verification
- Reload and restart failure analysis
- systemd error output review
- Service recovery after configuration fixes

### 2. Configuration Layer

- Nginx syntax validation using `nginx -t`
- Invalid directive identification
- Safe configuration cleanup
- Reload verification after correction

### 3. Filesystem and Permission Layer

- Web root permission checks
- Index file readability validation
- Ownership and access troubleshooting
- HTTP 403 root-cause confirmation

### 4. Verification Layer

- Local HTTP response testing
- Final `200 OK` confirmation
- Evidence-based before and after validation
- Clean incident closure

## 🛠️ Commands Used

### Check Nginx service status

```bash
systemctl status nginx
```

### Validate Nginx configuration

```bash
sudo nginx -t
```

### Reload Nginx safely

```bash
sudo systemctl reload nginx
```

### Check HTTP response

```bash
curl -I http://localhost
```

### Check listening port

```bash
ss -tulnp | grep :80
```

### Check web root and file permissions

```bash
ls -ld /var/www/html
ls -l /var/www/html/index.html
```

### Review Nginx logs

```bash
sudo tail -n 50 /var/log/nginx/error.log
sudo journalctl -u nginx
```

## 📌 Scenario Breakdown

### 1. Nginx 403 Forbidden - File Permission

> Nginx service was running successfully, but the web page returned `403 Forbidden`.

The investigation focused on file permissions, ownership, and web root access.  
The issue was fixed by correcting file access so Nginx could read and serve the index file properly.

**Skills demonstrated:**

- HTTP error troubleshooting
- Linux permission analysis
- Web root validation
- Before and after verification

### 2. Nginx Configuration Syntax Error

> Nginx reload failed after an invalid directive was added to the configuration file.

The issue was identified using `nginx -t`, traced to a bad configuration line, fixed by removing the invalid directive, and verified with a successful reload and HTTP response.

**Skills demonstrated:**

- Nginx config validation
- systemd reload failure troubleshooting
- Safe recovery workflow
- Error-output based root-cause analysis

## 🧠 Operational Skills Demonstrated

- Linux administration
- Nginx troubleshooting
- systemd service debugging
- Configuration validation
- Permission troubleshooting
- Log-based investigation
- Incident documentation
- Root-cause analysis
- Safe production-style recovery
- Final verification with command output

## ✅ Final Result

Both Nginx incidents were successfully investigated, fixed, and verified with clear evidence.

The scenarios demonstrate a practical Linux troubleshooting approach:

```text
Detect the issue → Confirm the symptom → Investigate the correct layer → Identify root cause → Apply fix → Verify recovery
```

## 👨‍💻 Author

**Aayush Pathak**  
Linux Server Administration Troubleshooting Lab
