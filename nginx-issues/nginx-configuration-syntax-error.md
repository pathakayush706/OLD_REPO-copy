# 🌐 Nginx Configuration Syntax Error

## Incident Summary

Nginx was running, but a configuration change introduced an invalid directive.

After the change, Nginx configuration validation failed and the service could not be reloaded safely.

This issue demonstrates how to troubleshoot Nginx reload failures using `nginx -t`, service status, and configuration file review.

---

## 🔴 Impact

- Nginx configuration validation failed
- Nginx reload failed
- New configuration could not be applied
- Existing service state was at risk if not validated before restart
- Issue was caused by invalid Nginx syntax

---

## 🧪 Symptom

Nginx reload failed after a configuration change:

    sudo systemctl reload nginx

Configuration test also failed:

    sudo nginx -t

The output showed an invalid directive inside the Nginx configuration.

---

## 🖼️ Screenshot - Reload Failed

![Nginx reload failed](../screenshots/nginx-configuration-syntax-error/nginx-reload-failed.png)

---

## 🔍 Investigation

Validated the Nginx configuration:

    sudo nginx -t

Checked the active Nginx site configuration:

    sudo tail -n 10 /etc/nginx/sites-available/localhost-only-lab.conf

The configuration contained an invalid directive:

    invalid_nginx_directive;

This line caused Nginx syntax validation to fail.

---

## 🖼️ Screenshot - Syntax Error Evidence

![Nginx syntax error evidence](../screenshots/nginx-configuration-syntax-error/nginx-test-shows-syntax-error.png)

---

## 🎯 Root Cause

The root cause was an invalid directive added to the Nginx site configuration file.

Nginx could not understand the directive, so configuration validation failed.

This was not a port issue, permission issue, or firewall issue.

---

## ✅ Fix Applied

Removed the invalid directive from the configuration file:

    sudo sed -i '/invalid_nginx_directive;/d' /etc/nginx/sites-available/localhost-only-lab.conf

Validated the configuration:

    sudo nginx -t

Reloaded Nginx safely:

    sudo systemctl reload nginx

---

## ✅ Verification

Verified Nginx configuration:

    sudo nginx -t

Verified local web response:

    curl -I http://localhost

Successful response:

    HTTP/1.1 200 OK
    Server: nginx

---

## 🖼️ Screenshot - Configuration Fixed

![Nginx config fixed and verified](../screenshots/nginx-configuration-syntax-error/nginx-config-fixed-200-ok.png)

---

## 🧰 Commands Used

Add invalid config line for lab scenario:

    echo 'invalid_nginx_directive;' | sudo tee -a /etc/nginx/sites-available/localhost-only-lab.conf

Test Nginx configuration:

    sudo nginx -t

Reload Nginx:

    sudo systemctl reload nginx

Review config ending:

    sudo tail -n 10 /etc/nginx/sites-available/localhost-only-lab.conf

Remove invalid directive:

    sudo sed -i '/invalid_nginx_directive;/d' /etc/nginx/sites-available/localhost-only-lab.conf

Verify HTTP response:

    curl -I http://localhost

---

## 🧠 Key Learning

Always run `nginx -t` before reloading or restarting Nginx after configuration changes.

A small syntax mistake can prevent Nginx from applying new configuration safely.

For Nginx configuration issues, always check:

- `nginx -t`
- systemd service output
- active site configuration
- error message line number
- final HTTP verification

---

## Final Result

Nginx configuration validation passed after removing the invalid directive.

Final verification:

    HTTP/1.1 200 OK
