# AWS Server Bot Traffic Control (Cloudflare + Nginx)

## Objective

Protect AWS EC2 websites from:

* Fake page views
* Scraping bots
* Spam traffic
* Bandwidth abuse
* Excessive data transfer charges

This setup is used when the frontend is hosted on **Cloudflare Pages or Nginx** and the backend is running on **AWS EC2 (Ubuntu + Nginx + PM2)**.

---

# Architecture

```text
Internet
   |
Cloudflare (Bot protection + WAF + Rate limit)
   |
AWS EC2 (Nginx)
   |
PM2
   |
Node.js Application
```

---

# Step 1: Enable Cloudflare Proxy

## DNS Settings

Cloudflare Dashboard → DNS

Ensure the records are **Proxied (Orange Cloud)**.

| Type | Name | Value         | Proxy   |
| ---- | ---- | ------------- | ------- |
| A    | @    | EC2_PUBLIC_IP | Proxied |
| A    | api  | EC2_PUBLIC_IP | Proxied |

This hides the real server IP and allows Cloudflare to filter traffic.

---

# Step 2: Enable Bot Fight Mode

## Navigation

```text
Security → Overview → Bot traffic
```

Enable:

* Bot Fight Mode → ON
* Block AI Bots → Block

## What it does

* Detects automated traffic
* Challenges suspicious bots
* Reduces fake page views
* Prevents unnecessary bandwidth usage

---

# Step 3: Create Rate Limiting Rule

## Navigation

```text
Security → Security rules → Rate limiting rules → Create rule
```

## Rule Configuration

| Field     | Value             |
| --------- | ----------------- |
| Rule name | limit-bot-traffic |
| Requests  | 100               |
| Period    | 1 minute          |
| Action    | Managed Challenge |

## Effect

If a single IP sends more than **100 requests in 1 minute**, Cloudflare will show a challenge page and block most automated bots.

---

# Step 4: Protect Static Assets

Create a custom WAF rule.

## Expression

```text
(http.request.uri.path contains ".jpg") or
(http.request.uri.path contains ".png") or
(http.request.uri.path contains ".webp") or
(http.request.uri.path contains ".mp4")
```

## Action

```text
Managed Challenge
```

This prevents bots from repeatedly downloading images and videos.

---

# Step 5: Enable Cloudflare Caching

## Navigation

```text
Caching → Cache Rules → Create rule
```

## Match

```text
*.jpg, *.png, *.webp, *.css, *.js
```

## Settings

| Setting           | Value    |
| ----------------- | -------- |
| Cache eligibility | Eligible |
| Edge TTL          | 1 month  |
| Browser TTL       | 1 day    |

## Benefit

Static files are served from Cloudflare’s CDN instead of the EC2 server, reducing AWS bandwidth costs.

---

# Step 6: Configure Nginx Rate Limiting

Edit Nginx config:

```bash
sudo nano /etc/nginx/nginx.conf
```

Inside the `http {}` block add:

```nginx
limit_req_zone $binary_remote_addr zone=api_limit:10m rate=5r/s;
```

---

## Apply to the website

Edit the server block:

```bash
sudo nano /etc/nginx/sites-available/client.conf
```

Add inside `location /`:

```nginx
location / {
    limit_req zone=api_limit burst=20 nodelay;
    try_files $uri $uri/ /index.html;
}
```

---

## Test and reload

```bash
sudo nginx -t
sudo systemctl reload nginx
```

---

# Step 7: Block Direct Access to EC2

Allow traffic only from Cloudflare IP ranges.

## Create Cloudflare IP file

```bash
sudo nano /etc/nginx/cloudflare-only.conf
```

Add:

```nginx
allow 173.245.48.0/20;
allow 103.21.244.0/22;
allow 103.22.200.0/22;
allow 103.31.4.0/22;
allow 141.101.64.0/18;
allow 108.162.192.0/18;
allow 190.93.240.0/20;
allow 188.114.96.0/20;
allow 197.234.240.0/22;
allow 198.41.128.0/17;
deny all;
```

Include it in the server block:

```nginx
server {
    listen 80;
    server_name example.com;

    include /etc/nginx/cloudflare-only.conf;
}
```

Reload:

```bash
sudo systemctl reload nginx
```

This prevents attackers from bypassing Cloudflare and hitting the EC2 IP directly.

---

# Step 8: Monitor Traffic

## Top IPs

```bash
sudo awk '{print $1}' /var/log/nginx/access.log | sort | uniq -c | sort -nr | head
```

## Live monitoring

```bash
sudo tail -f /var/log/nginx/access.log
```

## Bandwidth usage

Install vnstat:

```bash
sudo apt install vnstat -y
vnstat -d
```

Example output:

```text
day        rx      tx     total
22 Jul     1.2 GB  3.8 GB 5.0 GB
```

---

# Step 9: Block a Malicious IP

Temporary block:

```bash
sudo ufw deny from 1.2.3.4
```

Permanent Nginx block:

```nginx
deny 1.2.3.4;
```

Reload Nginx:

```bash
sudo systemctl reload nginx
```

---

# Step 10: Verify Protection

## Cloudflare

* Bot Fight Mode = Enabled
* Rate limiting rule = Active
* DNS records = Proxied

## Nginx

```bash
sudo nginx -t
```

## Browser test

Open the site and ensure:

* Pages load normally
* Images load correctly
* No challenge is shown for normal browsing

---

# Expected Result

| Before                   | After                    |
| ------------------------ | ------------------------ |
| High fake traffic        | Reduced bot traffic      |
| Increased AWS bandwidth  | Lower data transfer      |
| Repeated image downloads | Cached at Cloudflare     |
| Direct EC2 exposure      | Hidden behind Cloudflare |

Typical reduction: **60–90% of unwanted automated traffic**.

---

# Troubleshooting

## Real users are getting challenged

Increase the rate limit:

```text
200 requests / 1 minute
```

---

## API requests fail

Exclude API paths from rate limiting:

```text
Path does not contain /api/webhook
```

---

## Images still consume bandwidth

Check:

* DNS is Proxied
* Cache rule is active
* Response header contains `cf-cache-status: HIT`

---

# Quick Commands

## Check bandwidth

```bash
vnstat -d
```

## Check top IPs

```bash
sudo awk '{print $1}' /var/log/nginx/access.log | sort | uniq -c | sort -nr | head
```

## Reload Nginx

```bash
sudo systemctl reload nginx
```

## Test configuration

```bash
sudo nginx -t
```

---

# Interview Answer

**How do you control bot traffic on AWS?**

I place Cloudflare in front of the EC2 server, enable Bot Fight Mode, configure WAF rate limiting, and cache static assets at the edge. On the server side, I use Nginx rate limiting and allow only Cloudflare IP ranges to access the origin. This reduces fake traffic, prevents scraping, and significantly lowers AWS bandwidth and data transfer costs.

