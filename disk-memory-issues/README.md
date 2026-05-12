# 💽 Disk & Memory Troubleshooting Scenarios

[![Linux](https://img.shields.io/badge/Linux-Server%20Administration-orange?style=flat-square&logo=linux)](https://www.linux.org/)
[![Disk](https://img.shields.io/badge/Disk-Space%20Issues-blue?style=flat-square&logo=linux)](#)
[![Memory](https://img.shields.io/badge/Memory-Usage%20Issues-success?style=flat-square&logo=linux)](#)
[![Troubleshooting](https://img.shields.io/badge/Focus-Root%20Cause%20Analysis-purple?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Scenarios-2%20Production%20Cases-success?style=flat-square)](#)

Disk & Memory Troubleshooting Scenarios is a production-style Linux administration section focused on common server resource issues.
It demonstrates practical troubleshooting skills for disk space full errors, high memory usage, safe cleanup, process review, and clean post-fix verification.

## ✨ Highlights

- 💽 Realistic disk space failure troubleshooting
- 🧠 High memory usage investigation
- 🔍 Root-cause focused analysis
- 🛠️ Safe cleanup and recovery steps
- ✅ Before and after verification
- 📸 Screenshot-backed incident evidence
- 🚀 Interview-ready Linux administration documentation

## 🚨 Troubleshooting Scenarios

| Incident | Scenario | Focus Area |
|---|---|---|
| [Disk Space Full](disk-space-full.md) | Application cannot write files because the filesystem is full | Disk usage, large files, cleanup |
| [Memory Usage High](memory-usage-high.md) | Server becomes slow because memory usage is high | Memory usage, process check, recovery |

## 🏗️ Troubleshooting Coverage

This section covers the main layers involved in disk and memory incident handling:

### 1. Disk Space Layer

- Filesystem usage validation
- Disk full error confirmation
- Large file and directory checks
- Safe cleanup verification

### 2. Memory Layer

- Memory usage validation
- Process-level memory review
- Server slowdown investigation
- Post-fix memory verification

### 3. Verification Layer

- Re-test affected command
- Confirm disk or memory status after fix
- Validate the issue is no longer visible
- Capture before and after evidence

## 🛠️ Commands Used

### Check disk space usage

```bash
df -h
```

### Check directory size

```bash
du -sh /path/to/directory
```

### Check file size

```bash
ls -lh /path/to/file
```

### Remove test or unwanted files

```bash
rm /path/to/file
```

### Check memory usage

```bash
free -h
```

### Check running processes

```bash
top
```

## 📌 Scenario Breakdown

### 1. Disk Space Full

> The filesystem became full and the application could not write new files.

The investigation focuses on checking disk usage, identifying the location consuming space, removing unnecessary test data, and confirming that disk space is available again.

**Skills demonstrated:**

- Disk usage troubleshooting
- Filesystem validation
- Large file checks
- Safe cleanup verification

### 2. Memory Usage High

> The server became slow because memory usage was high.

The investigation focuses on checking available memory, reviewing running processes, stopping the test memory load, and confirming memory usage after recovery.

**Skills demonstrated:**

- Memory usage analysis
- Process monitoring
- Server slowdown troubleshooting
- Post-fix validation

## 🧠 Operational Skills Demonstrated

- Linux administration
- Disk space troubleshooting
- Memory usage analysis
- Process review
- Root-cause analysis
- Safe cleanup practice
- Incident documentation
- Before and after verification
- Final verification with command output

## ✅ Final Result

Both disk and memory incidents were successfully investigated, fixed, and verified with clear evidence.

The scenarios demonstrate a practical Linux troubleshooting approach:

```text
Detect resource issue → Confirm usage → Find root cause → Apply safe fix → Verify recovery
```

## 👨‍💻 Author

**Aayush Pathak**  
Linux Server Administration Troubleshooting Lab
