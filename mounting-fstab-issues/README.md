# 📦 Mounting & Fstab Troubleshooting Scenarios

[![Linux](https://img.shields.io/badge/Linux-Server%20Administration-orange?style=flat-square&logo=linux)](https://www.linux.org/)
[![Mount](https://img.shields.io/badge/Mount-Filesystem%20Issues-blue?style=flat-square&logo=linux)](#)
[![Fstab](https://img.shields.io/badge/Fstab-Boot%20Mount%20Config-success?style=flat-square&logo=linux)](#)
[![Troubleshooting](https://img.shields.io/badge/Focus-Root%20Cause%20Analysis-purple?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Scenarios-2%20Production%20Cases-success?style=flat-square)](#)

Mounting & Fstab Troubleshooting Scenarios is a production-style Linux administration section focused on common filesystem mount failures.  
It demonstrates practical troubleshooting skills for `/etc/fstab` mistakes, failed `mount -a` checks, missing mount points, incorrect filesystem types, and clean post-fix verification.

## ✨ Highlights

- 📦 Realistic mount failure scenarios
- 🔍 Root-cause focused investigation
- 🧾 `/etc/fstab` validation
- 🛠️ Safe test mount recovery steps
- ✅ Before and after verification
- 📸 Screenshot-backed incident evidence
- 🚀 Interview-ready Linux administration documentation

## 🚨 Troubleshooting Scenarios

| Incident | Scenario | Focus Area |
|---|---|---|
| [Fstab Mount Point Missing](fstab-mount-point-missing.md) | `mount -a` fails because the mount point directory does not exist | Mount point validation, fstab entry, recovery |
| [Fstab Wrong Filesystem Type](fstab-wrong-filesystem-type.md) | `mount -a` fails because the filesystem type is incorrect in `/etc/fstab` | Filesystem type, fstab correction, verification |

## 🏗️ Troubleshooting Coverage

This section covers the main layers involved in mounting and fstab incident handling:

### 1. Mount Point Layer

- Mount directory validation
- Missing mount point investigation
- `mount -a` failure confirmation
- Safe directory creation and retest

### 2. Fstab Configuration Layer

- `/etc/fstab` entry review
- Filesystem type validation
- Mount option checks
- Safe correction with backup awareness

### 3. Mount Verification Layer

- Manual mount validation
- Mounted filesystem checks
- Post-fix `mount -a` verification
- Clean incident closure with command output

## 🛠️ Commands Used

### Check fstab entry

```bash
grep /mnt/appdata /etc/fstab
```

### Test fstab mounts

```bash
sudo mount -a
```

### Check mount point directory

```bash
ls -ld /mnt/appdata
```

### Create missing mount point

```bash
sudo mkdir -p /mnt/appdata
```

### Check mounted filesystem

```bash
findmnt /mnt/appdata
```

### Check disk or mounted filesystem usage

```bash
df -h /mnt/appdata
```

### Unmount test mount

```bash
sudo umount /mnt/appdata
```

## 📌 Scenario Breakdown

### 1. Fstab Mount Point Missing

> The fstab entry was present, but the mount failed because the mount point directory was missing.

The investigation focuses on checking the fstab entry, reproducing the mount failure, validating the missing directory, creating the mount point, and confirming that the filesystem mounts successfully.

**Skills demonstrated:**

- Mount point troubleshooting
- Fstab entry validation
- `mount -a` failure analysis
- Safe mount recovery

### 2. Fstab Wrong Filesystem Type

> The mount point existed, but the fstab entry used the wrong filesystem type.

The investigation focuses on the failed `mount -a` output, checking the fstab line, correcting the filesystem type, and verifying that the mount works after the fix.

**Skills demonstrated:**

- Filesystem type troubleshooting
- Fstab syntax review
- Mount verification
- Configuration correction

## 🧠 Operational Skills Demonstrated

- Linux administration
- Fstab troubleshooting
- Mount failure debugging
- Filesystem validation
- Safe configuration changes
- Root-cause analysis
- Incident documentation
- Before and after verification
- Final verification with command output

## ✅ Final Result

Both mounting and fstab incidents are designed to be investigated, fixed, and verified with simple production-style commands.

The scenarios demonstrate a practical Linux troubleshooting approach:

```text
Detect mount failure → Check fstab → Confirm mount point or filesystem issue → Apply safe fix → Verify mount
```

## 👨‍💻 Author

**Aayush Pathak**  
Linux Server Administration Troubleshooting Lab
