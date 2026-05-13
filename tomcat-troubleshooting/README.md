# ☕ Tomcat Troubleshooting Scenarios

[![Linux](https://img.shields.io/badge/Linux-Server%20Administration-orange?style=flat-square&logo=linux)](https://www.linux.org/)
[![Tomcat](https://img.shields.io/badge/Tomcat-Application%20Server-blue?style=flat-square&logo=apachetomcat)](#)
[![Startup](https://img.shields.io/badge/Startup-Manual%20Scripts-success?style=flat-square&logo=linux)](#)
[![Troubleshooting](https://img.shields.io/badge/Focus-Root%20Cause%20Analysis-purple?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Scenarios-2%20Production%20Cases-success?style=flat-square)](#)

Tomcat Troubleshooting Scenarios is a production-style Linux administration section focused on common Apache Tomcat startup and access issues.  
It demonstrates practical troubleshooting skills for startup failures, port conflicts, application access problems, and clean post-fix verification.

## ✨ Highlights

- ☕ Realistic Tomcat startup failure scenarios
- 🔍 Root-cause focused investigation
- 🌐 Port and application access validation
- 🛠️ Simple startup recovery steps
- ✅ Before and after verification
- 📸 Screenshot-backed incident evidence
- 🚀 Interview-ready Linux administration documentation

## 🚨 Troubleshooting Scenarios

| Incident | Scenario | Focus Area |
|---|---|---|
| [Tomcat Service Not Running](tomcat-service-not-running.md) | Tomcat is stopped and the application URL is not reachable | Process status, application access, startup |
| [Tomcat Port Conflict](tomcat-port-conflict.md) | Tomcat fails to start because another process is already using port 8080 | Port check, process validation, startup recovery |

## 🏗️ Troubleshooting Coverage

This section covers the main layers involved in Tomcat incident handling:

### 1. Startup Layer

- Tomcat process validation
- Stopped application investigation
- Startup and recovery checks
- Difference between process status and application access

### 2. Port Layer

- Port 8080 availability check
- Process conflict validation
- Application listener verification
- Clean Tomcat startup after conflict removal

### 3. Application Access Layer

- Local URL testing
- HTTP response validation
- Browser or command-line access verification
- Before and after incident evidence

### 4. Verification Layer

- Confirm Tomcat process is running
- Confirm port 8080 is listening
- Confirm application URL is reachable
- Close the issue with final command output

## 🛠️ Commands Used

### Start Tomcat

```bash
/home/aayush-pathak/tomcat/bin/startup.sh
```

### Stop Tomcat

```bash
/home/aayush-pathak/tomcat/bin/shutdown.sh
```

### Check application URL

```bash
curl http://localhost:8080
```

### Check port 8080

```bash
ss -ltnp | grep 8080
```

### Check running Tomcat process

```bash
ps -ef | grep tomcat
```

## 📌 Scenario Breakdown

### 1. Tomcat Service Not Running

> Tomcat was stopped, so the application running on port 8080 was not reachable.

The investigation focuses on checking the URL failure, validating the Tomcat process status, starting Tomcat again, and confirming the application is reachable.

**Skills demonstrated:**

- Tomcat process troubleshooting
- Application access validation
- Tomcat startup recovery
- Before and after verification

### 2. Tomcat Port Conflict

> Tomcat failed to start because another process was already using port 8080.

The investigation focuses on checking the failed startup, identifying the process using port 8080, stopping the conflicting process, and starting Tomcat successfully.

**Skills demonstrated:**

- Port conflict troubleshooting
- Process validation
- Startup recovery
- Application listener verification

## 🧠 Operational Skills Demonstrated

- Linux administration
- Tomcat startup troubleshooting
- Process validation
- Port conflict analysis
- Application access testing
- Root-cause analysis
- Safe recovery practice
- Incident documentation
- Before and after verification
- Final verification with command output

## ✅ Final Result

Both Tomcat incidents can be investigated, fixed, and verified using simple Linux commands.

The scenarios demonstrate a practical Tomcat troubleshooting approach:

```text
Detect access failure → Check process → Check port → Apply fix → Verify application access
```

## 👨‍💻 Author

**Aayush Pathak**  
Linux Server Administration Troubleshooting Lab
