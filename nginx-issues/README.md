# 🌐 Nginx Troubleshooting Scenarios

This section contains production-style Nginx troubleshooting incidents focused on web server availability, HTTP errors, permissions, port binding, firewall access, configuration validation, and log-based investigation.

Each scenario is documented like a real Linux Operations incident:

    Symptom -> Investigation -> Root Cause -> Fix -> Verification

---

## 📌 Incident List

| Incident | Scenario | Focus Area |
|---|---|---|
| [Nginx 403 Forbidden - File Permission](nginx-403-forbidden-file-permission.md) | Nginx is running, but the website returns 403 Forbidden because the index file is not readable | File permissions |
| Nginx Localhost Works but Remote Access Fails | Website works on the server using localhost, but fails from another machine | Firewall / network access |
| Nginx Port Binding Conflict | Nginx fails to start because another process is already using port 80 | Port conflict |
| Nginx Configuration Syntax Error | Nginx reload or restart fails due to invalid configuration | Config validation |
| Nginx Wrong Document Root | Nginx serves the wrong page or wrong directory | Server block / document root |
| Nginx Log-Based Troubleshooting | Nginx error logs are used to identify service or access issues | Log investigation |

---

## 🧭 Nginx Troubleshooting Flow

    Client Request
        |
        v
    HTTP Response Check
        |
        v
    Nginx Service Status
        |
        v
    Port Listening Check
        |
        v
    Configuration Validation
        |
        v
    Web Root and Permission Check
        |
        v
    Firewall / Network Check
        |
        v
    Logs and Root Cause
        |
        v
    Fix and Verification

---

## 🧪 Common Commands

Check Nginx service:

    systemctl status nginx

Check local HTTP response:

    curl -I http://localhost

Check remote HTTP response:

    curl -I http://<server-ip>

Check listening port:

    ss -tulnp | grep :80

Validate Nginx configuration:

    sudo nginx -t

Check web root permission:

    ls -ld /var/www/html
    ls -l /var/www/html/index.html

Check Nginx logs:

    sudo tail -n 50 /var/log/nginx/error.log
    sudo journalctl -u nginx

---

## 🖼️ Screenshot Evidence Standard

Screenshots should be used only as proof of troubleshooting, not for every command.

For each incident, capture only:

1. Error before the fix
2. Root cause evidence
3. Successful verification after the fix

Screenshot folders should be named after the incident.

Example:

    ../screenshots/nginx-issues/nginx-403-forbidden-file-permission/before-403-forbidden.png
    ../screenshots/nginx-issues/nginx-403-forbidden-file-permission/permission-root-cause.png
    ../screenshots/nginx-issues/nginx-403-forbidden-file-permission/after-200-ok.png

---

## ✅ Completed Scenarios

- [Nginx 403 Forbidden - File Permission](nginx-403-forbidden-file-permission.md)

---

## 🚧 Upcoming Scenarios

- Nginx Localhost Works but Remote Access Fails
- Nginx Port Binding Conflict
- Nginx Configuration Syntax Error
- Nginx Wrong Document Root
- Nginx Log-Based Troubleshooting

---

## Key Learning

Nginx troubleshooting should follow a layer-by-layer process.

Do not guess the issue directly. First confirm the response, then check service status, port listening, configuration, permissions, firewall, and logs.
