# 🔐 SSH Troubleshooting Scenarios

[![Linux](https://img.shields.io/badge/Linux-Server%20Administration-orange?style=flat-square&logo=linux)](https://www.linux.org/)
[![OpenSSH](https://img.shields.io/badge/OpenSSH-Remote%20Access-blue?style=flat-square&logo=gnubash)](https://www.openssh.com/)
[![Systemd](https://img.shields.io/badge/Systemd-Service%20Recovery-success?style=flat-square&logo=linux)](#)
[![Security](https://img.shields.io/badge/Focus-Authentication%20%26%20Access-purple?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Scenarios-2%20Production%20Cases-success?style=flat-square)](#)

SSH Troubleshooting Scenarios is a production-style Linux administration section focused on real remote access failures, authentication issues, service recovery, and evidence-based root-cause analysis.  
It demonstrates practical troubleshooting skills using OpenSSH, Linux permissions, systemd, port validation, logs, and secure access verification.

## ✨ Highlights

- 🔐 Realistic SSH access failure scenarios
- 🔍 Root-cause focused investigation
- 🛠️ Linux service and authentication debugging
- 🔑 SSH key permission troubleshooting
- 📡 Port and service availability validation
- 📸 Screenshot-backed incident evidence
- 🚀 Interview-ready Linux administration documentation

## 🚨 Troubleshooting Scenarios

| Incident | Scenario | Focus Area |
|---|---|---|
| [SSH Permission Denied - Publickey](ssh-permission-denied-publickey.md) | SSH server is reachable, but login fails because the private key permissions are insecure and the key is ignored | SSH keys, file permissions, authentication |
| [SSH Connection Refused - Service Down](ssh-connection-refused-service-down.md) | SSH connection fails because the SSH service is stopped or port 22 is not listening | systemd, service recovery, port validation |

## 🏗️ Troubleshooting Coverage

This section covers the main layers involved in SSH incident handling:

### 1. Authentication Layer

- Public key authentication failure analysis
- Correct user and key validation
- SSH client error output review
- Login verification after fix

### 2. Permission Layer

- Private key permission checks
- `.ssh` directory permission validation
- `authorized_keys` ownership verification
- Secure SSH file access correction

### 3. Service Layer

- SSH service status verification
- systemd failure analysis
- Service start and restart recovery
- Boot-time service enablement checks

### 4. Network and Port Layer

- Port 22 listening validation
- Connection refused troubleshooting
- Local SSH reachability testing
- Service binding confirmation

### 5. Verification Layer

- Final SSH login confirmation
- Remote command execution test
- User identity verification using `whoami`
- Clean incident closure with screenshot evidence

## 🛠️ Commands Used

### Test SSH login with a private key

```bash
ssh -i /root/ssh-lab-keys/sshlab_key sshlabuser@localhost
```

### Run SSH with strict key usage

```bash
ssh -i /root/ssh-lab-keys/sshlab_key -o IdentitiesOnly=yes sshlabuser@localhost
```

### Check private key permission

```bash
ls -l /root/ssh-lab-keys/sshlab_key
```

### Fix private key permission

```bash
chmod 600 /root/ssh-lab-keys/sshlab_key
```

### Check SSH service status

```bash
systemctl status ssh
systemctl status sshd
```

### Start or restart SSH service

```bash
sudo systemctl start ssh
sudo systemctl restart ssh
```

### Check if SSH is listening on port 22

```bash
ss -tulnp | grep :22
```

### Review SSH service logs

```bash
sudo journalctl -u ssh
sudo journalctl -u sshd
```

## 📌 Scenario Breakdown

### 1. SSH Permission Denied - Publickey

> SSH login failed with `Permission denied (publickey)` even though the server was reachable.

The investigation focused on the private key file permission.  
The key was too open, so the SSH client refused to use it during authentication.

The issue was fixed by changing the private key permission to `600` and retrying the SSH login.

**Skills demonstrated:**

- SSH key authentication troubleshooting
- Linux file permission analysis
- Secure private key handling
- Authentication failure verification

### 2. SSH Connection Refused - Service Down

> SSH connection failed with `Connection refused` because the SSH service was not accepting connections.

The investigation focused on service status, port listening state, and systemd recovery.  
The issue was fixed by starting the SSH service and verifying that port 22 was listening again.

**Skills demonstrated:**

- SSH service troubleshooting
- systemd service recovery
- Port listening validation
- Remote access verification

## 🧠 Operational Skills Demonstrated

- Linux administration
- SSH troubleshooting
- OpenSSH authentication debugging
- Linux permission troubleshooting
- systemd service recovery
- Port and process validation
- Log-based investigation
- Root-cause analysis
- Secure access verification
- Incident documentation

## ✅ Final Result

Both SSH incidents were investigated, fixed, and verified with clear command output and screenshot evidence.

The scenarios demonstrate a practical Linux troubleshooting approach:

```text
Detect the access issue → Confirm the error → Identify the failing layer → Fix the root cause → Verify SSH recovery
```

## 👨‍💻 Author

**Aayush Pathak**  
Linux Server Administration Troubleshooting Lab
