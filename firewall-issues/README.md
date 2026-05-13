# 🔥 Firewall Troubleshooting Scenarios

[![Linux](https://img.shields.io/badge/Linux-Server%20Administration-orange?style=flat-square&logo=linux)](https://www.linux.org/)
[![Firewall](https://img.shields.io/badge/Firewall-Port%20Access-blue?style=flat-square)](#)
[![iptables](https://img.shields.io/badge/iptables-Traffic%20Filtering-success?style=flat-square)](#)
[![Networking](https://img.shields.io/badge/Focus-Network%20Troubleshooting-purple?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Scenarios-2%20Production%20Cases-success?style=flat-square)](#)

Firewall Troubleshooting Scenarios is a production-style Linux administration section focused on service access failures caused by firewall rules.

This section demonstrates how to confirm that a service is running, verify that a port is listening, identify firewall blocking, apply a simple fix, and verify access again.

The commands are intentionally simple, safe for a lab VM, and interview-friendly.

---

## ✨ Highlights

- 🔥 Realistic firewall access failure scenarios
- 🔍 Root-cause focused investigation
- 📡 Port listening validation
- 🧱 Firewall rule troubleshooting
- 🛠️ Simple break and fix commands
- 📸 Screenshot-backed incident evidence
- 🚀 Interview-ready Linux administration documentation

---

## 🚨 Troubleshooting Scenarios

| Incident | Scenario | Focus Area |
|---|---|---|
| [HTTP Port 80 Blocked](firewall-http-port-blocked.md) | Nginx is running, but HTTP access fails because firewall blocks port `80` | firewall rules, port 80, Nginx access |
| [ICMP Ping Blocked](firewall-icmp-ping-blocked.md) | Ping fails because ICMP echo requests are blocked by firewall rules | firewall rules, ICMP, ping troubleshooting |

---

## 🏗️ Troubleshooting Coverage

This section covers the main layers involved in firewall incident handling.

### 1. Service Layer

- Confirm the service is running
- Check whether the application is active
- Avoid blaming firewall before checking the service

### 2. Port Layer

- Confirm the required port is listening
- Check port `80` for HTTP traffic
- Verify ICMP connectivity using ping

### 3. Firewall Layer

- Check firewall rules
- Identify blocked traffic
- Remove the blocking rule
- Allow required access

### 4. Verification Layer

- Retest access after the fix
- Confirm the port is reachable
- Capture before-and-after screenshots
- Close the incident with proof

---

## 🛠️ Commands Used

### Check Nginx service

    systemctl status nginx

### Check port 80

    ss -tulnp | grep :80

### Test HTTP access

    curl -I http://localhost

### Check firewall rules

    sudo iptables -L

### Block HTTP port 80 for lab

    sudo iptables -I INPUT -p tcp --dport 80 -j REJECT

### Fix HTTP port 80 access

    sudo iptables -D INPUT -p tcp --dport 80 -j REJECT

### Test ICMP connectivity

    ping -c 4 localhost

### Block ICMP ping for lab

    sudo iptables -I INPUT -p icmp --icmp-type echo-request -j DROP

### Fix ICMP ping access

    sudo iptables -D INPUT -p icmp --icmp-type echo-request -j DROP

---

## 📌 Scenario Breakdown

### 1. HTTP Port 80 Blocked

> Nginx was running, but HTTP access failed because firewall rules blocked port `80`.

The investigation focuses on checking the service, checking the listening port, checking firewall rules, removing the blocking rule, and verifying HTTP access again.

**Skills demonstrated:**

- Firewall troubleshooting
- HTTP port validation
- Nginx access verification
- Root-cause explanation

### 2. ICMP Ping Blocked

> Ping failed because ICMP echo requests were blocked by firewall rules.

The investigation focuses on testing ICMP connectivity, checking firewall rules, removing the ICMP block, and verifying ping access again.

**Skills demonstrated:**

- ICMP troubleshooting
- Firewall rule validation
- Ping connectivity testing
- Simple production-style investigation

---

## 🧠 Operational Skills Demonstrated

- Linux administration
- Firewall troubleshooting
- iptables rule validation
- Port listening checks
- HTTP access testing
- Service vs firewall issue isolation
- Root-cause analysis
- Incident documentation
- Interview-ready troubleshooting explanation

---

## 🗣️ Interview Explanation

A firewall issue should not be guessed directly.

First, I confirm the service is running. Then I check whether the required port is listening. After that, I test access using `curl`. If the service and port are healthy but access still fails, I check firewall rules. Once I find the blocking rule, I remove it and verify access again.

---

## ✅ Final Result

Both firewall incidents are designed to show a simple troubleshooting flow:

    Confirm service → Confirm port → Test access → Check firewall → Fix rule → Verify access

---

## 👨‍💻 Author

**Aayush Pathak**  
Linux Server Administration Troubleshooting Lab
