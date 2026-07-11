# Production Issues (Real-Time Troubleshooting)

This document contains real production issues I have worked on as a DevOps Engineer.

---

# Issue 1 - SSL Certificate Issue

## Interview Question

Tell me about a production issue you solved.

---

## Situation

The website was showing SSL errors after deployment.

---

## Root Cause

The SSL certificate was either missing, expired, or Cloudflare SSL mode did not match the origin server configuration.

---

## Troubleshooting Steps

- Checked website in browser
- Verified SSL certificate
- Checked Nginx configuration
- Verified Cloudflare SSL Mode
- Checked Certbot status
- Restarted Nginx

---

## Commands Used

```bash
sudo nginx -t

sudo certbot certificates

sudo systemctl restart nginx
```

---

## Resolution

Generated a new SSL certificate using Certbot and configured Cloudflare SSL mode correctly.

The website became accessible over HTTPS.

---

# Issue 2 - Website Showing 502 Bad Gateway

## Situation

Users were getting a 502 Bad Gateway error.

---

## Root Cause

The backend application had stopped.

---

## Troubleshooting Steps

- Checked PM2 status
- Reviewed PM2 logs
- Verified backend port
- Restarted application
- Verified Nginx configuration

---

## Commands

```bash
pm2 status

pm2 logs

pm2 restart app

sudo nginx -t
```

---

## Resolution

Restarted the backend application and confirmed the API was working.

---

# Issue 3 - DNS Not Resolving

## Situation

The domain was not opening after deployment.

---

## Root Cause

DNS records were not updated correctly.

---

## Troubleshooting Steps

- Verified A Record
- Verified CNAME
- Checked DNS propagation
- Verified Cloudflare settings

---

## Commands

```bash
dig domain.com

nslookup domain.com
```

---

## Resolution

Updated the DNS records and waited for propagation.

The website became accessible.

---

# Issue 4 - React Website Showing Blank Page

## Root Cause

Incorrect Nginx configuration.

---

## Resolution

Configured

```nginx
location / {

try_files $uri $uri/ /index.html;

}
```

Restarted Nginx.

The React application loaded successfully.

---

# Common Production Issues

- SSL Certificate Expired
- Nginx Configuration Error
- PM2 Process Stopped
- DNS Propagation Delay
- Cloudflare SSL Mismatch
- API Not Responding
- High CPU Usage
- Disk Full
- Permission Issues
- Port Already in Use

---

# Troubleshooting Checklist

Website Down

↓

Check Browser

↓

Ping Domain

↓

DNS

↓

Cloudflare

↓

SSH

↓

PM2

↓

Nginx

↓

Logs

↓

SSL

↓

Restart

↓

Validate

---

# Interview Tips

✔ Never panic during production issues.

✔ Follow a structured troubleshooting approach.

✔ Check logs before restarting services.

✔ Verify the root cause before applying fixes.

✔ Validate the application after every change.
