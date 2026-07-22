# Cloudflare Bandwidth Optimization (Step 4 & Step 5)

## Step 4 - WAF Rule (Bot Protection)

### Purpose
Protect images and videos from excessive bot downloads and reduce bandwidth usage.

### Location
Cloudflare → Security → Security Rules → Create Rule

### Rule Name
Protect-Static-Assets

### Expression
(http.request.uri.path contains ".jpg") or
(http.request.uri.path contains ".png") or
(http.request.uri.path contains ".webp") or
(http.request.uri.path contains ".svg") or
(http.request.uri.path contains ".mp4")

### Action
Managed Challenge

### Benefits
- Reduces bot traffic
- Prevents image scraping
- Saves bandwidth
- Protects server resources
- Real users are not affected

### Interview Answer
In Cloudflare, I create WAF rules with Managed Challenge to protect static assets such as images and videos from automated bot traffic. This helps reduce bandwidth consumption and improves website security.

---

## Step 5 - Cache Rule (Bandwidth Saving)

### Purpose
Serve static files directly from Cloudflare CDN instead of the origin server.

### Location
Cloudflare → Caching → Cache Rules → Create Rule

### Rule Name
Cache-Static-Assets

### Match Condition
File Extension:

- jpg
- png
- webp
- svg
- css
- js

### Cache Settings

Cache Eligibility:
Eligible for Cache

Edge TTL:
1 Month

Browser TTL:
1 Day

### Benefits
- Reduces AWS/Server bandwidth usage
- Faster website loading
- Lower infrastructure cost
- Less load on origin server

### Example

Without Cache:
User → Cloudflare → AWS Server

With Cache:
User → Cloudflare Cache

### Verification

Press F12 → Network → Select Image

Check Header:

cf-cache-status: HIT

Meaning:
Image is served from Cloudflare cache instead of the server.

### Interview Answer
I use Cloudflare Cache Rules to cache static assets such as images, CSS, and JavaScript files. This reduces origin server requests, improves website performance, and significantly lowers bandwidth consumption.

---

## Recommended Production Setup

### Bot Protection
- Bot Fight Mode = ON
- Block AI Bots = ON
- WAF Rule = Managed Challenge

### Caching
- Cache static assets
- Edge TTL = 1 Month
- Browser TTL = 1 Day

### Result
- Reduced bot traffic
- Reduced bandwidth usage
- Faster website performance
- Lower AWS/Hosting cost
