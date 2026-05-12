# 📜 Logs & Permission Troubleshooting Scenarios

[![Linux](https://img.shields.io/badge/Linux-Server%20Administration-orange?style=flat-square&logo=linux)](https://www.linux.org/)
[![Logs](https://img.shields.io/badge/Logs-/var%2Flog-blue?style=flat-square&logo=linux)](#)
[![Permissions](https://img.shields.io/badge/Permissions-Access%20Control-success?style=flat-square&logo=linux)](#)
[![Troubleshooting](https://img.shields.io/badge/Focus-Root%20Cause%20Analysis-purple?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Scenarios-2%20Production%20Cases-success?style=flat-square)](#)

Logs & Permission Troubleshooting Scenarios is a production-style Linux administration section focused on real log access failures, permission denied errors, ownership mistakes, and safe recovery.  
It demonstrates practical troubleshooting skills using Linux file permissions, ownership checks, log directory validation, application user testing, and clean post-fix verification.

## ✨ Highlights

- 📜 Realistic log permission failure scenarios
- 🔍 Root-cause focused investigation
- 🔐 File and directory permission troubleshooting
- 👤 Application user access validation
- 🛠️ Safe permission and ownership fixes
- ✅ Before and after verification
- 📸 Screenshot-backed incident evidence
- 🚀 Interview-ready Linux administration documentation

## 🚨 Troubleshooting Scenarios

| Incident | Scenario | Focus Area |
|---|---|---|
| [Log File Permission Denied](logs-file-permission-denied.md) | Application user cannot read the log file because the file permission is too restrictive | File permission, ownership, read access |
| [Log Directory Write Permission Denied](logs-directory-write-permission-denied.md) | Application user cannot create or write logs because the log directory is owned by the wrong user | Directory permission, ownership, write access |

## 🏗️ Troubleshooting Coverage

This section covers the main layers involved in log permission incident handling:

### 1. Log Access Layer

- Log file read failure verification
- Permission denied error confirmation
- Application user access testing
- Difference between root access and normal user access

### 2. File Permission Layer

- Log file permission checks
- Owner and group validation
- Read permission troubleshooting
- Safe permission correction without using risky access

### 3. Directory Permission Layer

- Log directory ownership checks
- Write access validation
- Application log creation testing
- Directory-level permission recovery

### 4. Verification Layer

- Re-test log read access
- Re-test log file creation
- Confirm correct owner and permission
- Evidence-based before and after validation
- Clean incident closure

## 🛠️ Commands Used

### Check log file permission

```bash
ls -l /var/log/loglab/app.log
```

### Check log directory permission

```bash
ls -ld /var/log/loglab
```

### Read log file as application user

```bash
sudo -u loglabuser tail -n 5 /var/log/loglab/app.log
```

### Test log file creation as application user

```bash
sudo -u loglabuser touch /var/log/loglab/app-new.log
```

### Fix log file ownership

```bash
sudo chown loglabuser:loglabuser /var/log/loglab/app.log
```

### Fix log file permission

```bash
sudo chmod 640 /var/log/loglab/app.log
```

### Fix log directory ownership

```bash
sudo chown loglabuser:loglabuser /var/log/loglab
```

### Fix log directory permission

```bash
sudo chmod 750 /var/log/loglab
```

## 📌 Scenario Breakdown

### 1. Log File Permission Denied

> The log file existed, but the application user could not read it.

The investigation focused on file ownership and permission.  
The issue was fixed by correcting the log file owner and applying safe read permission for the application user.

**Skills demonstrated:**

- Log file access troubleshooting
- Linux permission analysis
- Ownership validation
- User-based verification

### 2. Log Directory Write Permission Denied

> The application user could not create or write log files inside the log directory.

The investigation focused on directory ownership and write permission.  
The issue was fixed by assigning the log directory to the correct application user and applying safe directory permissions.

**Skills demonstrated:**

- Directory permission troubleshooting
- Log write failure analysis
- Safe ownership correction
- Before and after verification

## 🧠 Operational Skills Demonstrated

- Linux administration
- Log access troubleshooting
- File permission debugging
- Directory permission debugging
- Ownership validation
- Application user testing
- Root-cause analysis
- Incident documentation
- Safe production-style recovery
- Final verification with command output

## ✅ Final Result

Both logs and permission incidents were successfully investigated, fixed, and verified with clear evidence.

The scenarios demonstrate a practical Linux troubleshooting approach:

```text
Detect the permission issue → Confirm the affected user → Check ownership → Check permissions → Apply safe fix → Verify access
```

## 👨‍💻 Author

**Aayush Pathak**  
Linux Server Administration Troubleshooting Lab
