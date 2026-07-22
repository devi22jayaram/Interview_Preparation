# Reduce Bot Traffic and Bandwidth Cost (Cloudflare + Nginx)

## Problem

Some websites receive fake traffic from bots, which increases:

* Page views
* Image requests
* Data transfer (bandwidth)
* VPS/AWS monthly cost

The goal is to stop suspicious traffic before it reaches the server.

---

# Cloudflare Protection (Free Plan)

## Enable Bot Fight Mode

### Path

Security → Overview → Detection tools → Bot traffic

### Settings

* Block AI bots → **Block**
* Bot Fight Mode → **ON**

### What it does

* Detects automated traffic
* Challenges suspicious bots
* Prevents scraping and fake page views
* Reduces unnecessary bandwidth usage

---

# Create Rate Limiting Rule

### Path

Security → Security rules → Rate limiting rules → Create rule

### Rule values

| Field     | Value             |
| --------- | ----------------- |
| Rule name | limit-bot-traffic |
| Requests  | 100               |
| Period    | 1 minute          |
| Action    | Managed Challenge |

### What it does

* Allows normal users
* Challenges IPs sending too many requests
* Prevents bots from repeatedly loading pages and images

---

# Why use Managed Challenge?

Managed Challenge is safer than Block:

* Real users usually pass automatically
* Suspicious bots fail the verification
* Traffic is stopped at Cloudflare edge
* The server does not spend bandwidth

---

# Nginx Backup Protection

## Add in nginx.conf (inside http block)

```nginx
limit_req_zone $binary_remote_addr zone=api:10m rate=5r/s;
```

## Add inside server block

```nginx
location / {
    limit_req zone=api burst=20 nodelay;
    try_files $uri $uri/ /index.html;
}
```

## Reload Nginx

```bash
sudo nginx -t
sudo systemctl reload nginx
```

This limits excessive requests directly on the server.

---

# Verify Cloudflare Proxy

### Path

DNS → Records

Make sure the record is **Proxied (orange cloud)**.

If it is gray, traffic bypasses Cloudflare and protection will not work.

---

# Monitor Bandwidth

## Install vnStat

```bash
sudo apt install vnstat -y
```

## Check daily usage

```bash
vnstat -d
```

Example:

```text
day        rx      tx     total
22 Jul     1.2 GB  3.8 GB 5.0 GB
```

Use this to track whether bot traffic has decreased.

---

# Recommended Production Settings

| Setting         | Value                  |
| --------------- | ---------------------- |
| Bot Fight Mode  | ON                     |
| Block AI Bots   | Block                  |
| Rate Limit      | 100 requests/minute/IP |
| Action          | Managed Challenge      |
| DNS Proxy       | Orange cloud           |
| Nginx limit_req | Enabled                |

---

# Real-World Note

I enabled Cloudflare Bot Fight Mode and rate limiting to reduce fake bot traffic that was increasing bandwidth and data transfer costs. This helps protect the website from automated scraping and repeated page requests while allowing normal users to access the site without interruption.

---

# Quick 5-Minute Checklist

* [ ] Enable Bot Fight Mode
* [ ] Keep Block AI Bots = Block
* [ ] Create rate limit rule (100 req/min)
* [ ] Use Managed Challenge action
* [ ] Verify DNS is proxied
* [ ] Reload Nginx after adding limit_req
* [ ] Monitor bandwidth with vnstat
