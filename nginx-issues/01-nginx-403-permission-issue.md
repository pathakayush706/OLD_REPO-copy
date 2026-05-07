# Issue 01: Nginx 403 Forbidden Due To File Permission

## Issue

Website was returning 403 Forbidden.

## Symptoms

User reported that the website was not loading properly.

When checked locally:

```bash
curl -I http://localhost
```

Output:

```text
HTTP/1.1 403 Forbidden
```

## Commands Used

```bash
curl -I http://localhost
systemctl status nginx
ss -tulnp | grep :80
ls -l /var/www/html/index.html
tail -n 50 /var/log/nginx/error.log
```

## Observation

Nginx service was running.

Port 80 was listening.

But curl returned 403 Forbidden.

The index.html file had incorrect permissions.

## Root Cause

The file `/var/www/html/index.html` did not have read permission, so nginx could not serve the file.

## Fix

```bash
sudo chmod 644 /var/www/html/index.html
```

## Verification

```bash
curl -I http://localhost
```

After fixing permission, the output returned:

```text
HTTP/1.1 200 OK
```

## Interview Explanation

I first checked the website locally using curl and got 403 Forbidden.

This means nginx was reachable, but access to the file was denied.

Then I checked nginx service and confirmed it was running.

I checked port 80 and confirmed nginx was listening.

After that, I checked the permission of index.html and found incorrect permissions.

I fixed the permission using chmod 644 and verified again using curl.

After the fix, curl returned 200 OK.
