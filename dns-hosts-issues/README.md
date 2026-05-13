# 🌐 DNS & Hosts Troubleshooting Scenarios

[![Linux](https://img.shields.io/badge/Linux-Server%20Administration-orange?style=flat-square&logo=linux)](https://www.linux.org/)
[![DNS](https://img.shields.io/badge/DNS-Name%20Resolution-blue?style=flat-square&logo=linux)](#)
[![Hosts](https://img.shields.io/badge/Hosts-/etc%2Fhosts-success?style=flat-square&logo=linux)](#)
[![Troubleshooting](https://img.shields.io/badge/Focus-Root%20Cause%20Analysis-purple?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Scenarios-2%20Production%20Cases-success?style=flat-square)](#)

DNS & Hosts Troubleshooting Scenarios is a production-style Linux administration section focused on hostname resolution issues, wrong `/etc/hosts` entries, missing host mappings, and simple application connectivity checks.

These scenarios use safe local test hostnames and avoid changing the real `localhost` entry.

## ✨ Highlights

- 🌐 Realistic hostname resolution failures
- 🧾 `/etc/hosts` troubleshooting
- 🔍 Simple root-cause investigation
- 🛠️ Safe host entry correction
- ✅ Before and after verification
- 📸 Screenshot-backed incident evidence
- 🚀 Interview-ready Linux troubleshooting documentation

## 🚨 Troubleshooting Scenarios

| Incident | Scenario | Focus Area |
|---|---|---|
| [Wrong Hosts File IP Entry](dns-wrong-hosts-entry.md) | Application hostname points to the wrong IP address in `/etc/hosts` | Hosts file, wrong IP, curl failure |
| [Missing Hosts File Entry](dns-missing-hosts-entry.md) | Internal hostname does not resolve because the hosts entry is missing | Hosts file, name resolution, hostname fix |

## 🏗️ Troubleshooting Coverage

This section covers the main layers involved in DNS and hosts file troubleshooting:

### 1. Hostname Resolution Layer

- Hostname access failure validation
- Wrong IP mapping checks
- Missing host entry checks
- Difference between working IP access and failed hostname access

### 2. Hosts File Layer

- `/etc/hosts` entry validation
- Wrong hostname-to-IP mapping investigation
- Safe hosts file backup
- Correct host entry update

### 3. Application Access Layer

- Local test application validation
- Curl-based access checks
- Port listening verification
- Final hostname-based verification

### 4. Verification Layer

- Confirm application port is listening
- Confirm hostname access works
- Confirm corrected `/etc/hosts` entry
- Before and after screenshot evidence

## 🛠️ Commands Used

### Check hosts file entry

```bash
cat /etc/hosts
```

### Test hostname access

```bash
curl http://app.local:8081
```

### Test IP access

```bash
curl http://127.0.0.1:8081
```

### Check listening port

```bash
ss -ltnp | grep 8081
```

### Backup hosts file

```bash
sudo cp /etc/hosts /etc/hosts.bak
```

### Edit hosts file safely

```bash
sudo nano /etc/hosts
```

## 📌 Scenario Breakdown

### 1. Wrong Hosts File IP Entry

> The application was running, but the hostname failed because `/etc/hosts` pointed it to the wrong IP address.

The investigation focuses on confirming that the application works by IP, checking the hosts file entry, correcting the wrong IP, and verifying hostname access again.

**Skills demonstrated:**

- Hosts file troubleshooting
- Wrong IP mapping analysis
- Curl-based validation
- Safe configuration correction

### 2. Missing Hosts File Entry

> The application was reachable by IP, but the internal hostname failed because the hosts file entry was missing.

The investigation focuses on confirming IP access, checking `/etc/hosts`, adding the missing hostname entry, and verifying the hostname-based request.

**Skills demonstrated:**

- Hostname resolution troubleshooting
- Missing entry investigation
- Safe hosts file update
- Before and after verification

## 🧠 Operational Skills Demonstrated

- Linux administration
- DNS troubleshooting basics
- Hosts file validation
- Application connectivity checks
- Root-cause analysis
- Safe configuration backup
- Incident documentation
- Final verification with command output

## ✅ Final Result

Both DNS and hosts file incidents demonstrate a practical Linux troubleshooting approach:

```text
Confirm app is running → Test hostname access → Check hosts entry → Fix mapping → Verify access
```

## 👨‍💻 Author

**Aayush Pathak**  
Linux Server Administration Troubleshooting Lab
