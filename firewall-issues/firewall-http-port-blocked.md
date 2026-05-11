# 🔥 Firewall HTTP Port 80 Blocked

## Incident Summary

Nginx was running, but HTTP access on port `80` was failing.

The web service was active and port `80` was listening, but a firewall rule blocked HTTP traffic.

This scenario demonstrates a common Linux firewall issue where the service is healthy, but access fails because the firewall rejects the port.

---

## 🔴 Impact

- Website access failed on HTTP port `80`
- Nginx service was running
- Port `80` was listening
- HTTP request failed because firewall blocked traffic
- Issue was caused by a firewall rule, not by Nginx configuration

---

## 🧪 Symptom

HTTP access failed while testing the local web server:

    curl -I http://127.0.0.1

The request failed instead of returning a normal Nginx response.

Nginx service was checked:

    systemctl is-active nginx

Port `80` was also checked:

    ss -tulnp | grep :80

Nginx was active and port `80` was listening, so the issue was not a service failure.

---

## 🖼️ Screenshot - HTTP Port Blocked

![Firewall HTTP port blocked](../screenshots/firewall-issues/firewall-http-port-blocked/firewall-http-port-blocked-before.png)

---

## 🔍 Investigation

Checked Nginx service status:

    systemctl is-active nginx

Expected result:

    active

Checked whether port `80` was listening:

    ss -tulnp | grep :80

Tested HTTP access:

    curl -I http://127.0.0.1

Checked firewall rules:

    sudo iptables -L INPUT -n

The firewall had a rule rejecting TCP traffic on port `80`.

Because Nginx was active and port `80` was listening, the investigation confirmed that the failure was caused by firewall filtering.

---

## 🎯 Root Cause

The root cause was a firewall rule blocking HTTP traffic on port `80`.

Nginx was healthy, and the port was listening, but the firewall rejected the connection.

This was not a Nginx configuration issue, service issue, or port listening issue.

---

## ✅ Fix Applied

Removed the firewall rule blocking HTTP port `80`:

    sudo iptables -D INPUT -p tcp --dport 80 -j REJECT

Verified HTTP access again:

    curl -I http://127.0.0.1

Expected result:

    HTTP/1.1 200 OK
    Server: nginx

---

## ✅ Verification

Checked that Nginx was active:

    systemctl is-active nginx

Confirmed port `80` was listening:

    ss -tulnp | grep :80

Confirmed HTTP access was restored:

    curl -I http://127.0.0.1

Successful response:

    HTTP/1.1 200 OK
    Server: nginx

---

## 🖼️ Screenshot - HTTP Access Restored

![Firewall HTTP port fixed](../screenshots/firewall-issues/firewall-http-port-blocked/firewall-http-port-blocked-after.png)

---

## 🧰 Commands Used

Create screenshot folder:

    mkdir -p /home/aayush-pathak/linux-production-troubleshooting-lab-copy/screenshots/firewall-issues/firewall-http-port-blocked

Create the issue:

    sudo iptables -I INPUT -p tcp --dport 80 -j REJECT

Check Nginx service:

    systemctl is-active nginx

Check port `80`:

    ss -tulnp | grep :80

Test HTTP access during issue:

    curl -I http://127.0.0.1

Check firewall rules:

    sudo iptables -L INPUT -n

Fix the issue:

    sudo iptables -D INPUT -p tcp --dport 80 -j REJECT

Verify HTTP access after fix:

    curl -I http://127.0.0.1

---

## 📸 Screenshot Steps

### Before Fix Screenshot

Run these commands after creating the issue:

    systemctl is-active nginx
    ss -tulnp | grep :80
    curl -I http://127.0.0.1
    sudo iptables -L INPUT -n

Save the screenshot as:

    /home/aayush-pathak/linux-production-troubleshooting-lab-copy/screenshots/firewall-issues/firewall-http-port-blocked/firewall-http-port-blocked-before.png

### After Fix Screenshot

Run these commands after applying the fix:

    systemctl is-active nginx
    ss -tulnp | grep :80
    curl -I http://127.0.0.1

Save the screenshot as:

    /home/aayush-pathak/linux-production-troubleshooting-lab-copy/screenshots/firewall-issues/firewall-http-port-blocked/firewall-http-port-blocked-after.png

---

## 🧠 Key Learning

When a website is not accessible, do not directly blame Nginx.

Check in this order:

- service status
- listening port
- HTTP response
- firewall rules

If the service is active and the port is listening, but access still fails, firewall rules are a strong suspect.

---

## 🗣️ Interview Explanation

Nginx was active and port `80` was listening, but HTTP access was failing. I checked the service first, then checked the listening port. After confirming both were fine, I tested HTTP access with `curl` and checked firewall rules. I found that the firewall was blocking port `80`, removed the blocking rule, and verified that HTTP access returned `200 OK`.

---

## Final Result

HTTP access was restored after removing the firewall rule blocking port `80`.

Final verification:

    HTTP/1.1 200 OK
