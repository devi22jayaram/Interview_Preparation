# Edge TTL vs Browser TTL

## Edge TTL

- Cache location: Cloudflare CDN
- Purpose: Reduce origin server requests
- Saves AWS/Hostinger bandwidth
- Example: 1 month

## Browser TTL

- Cache location: User browser
- Purpose: Faster repeat visits
- Reduces requests to Cloudflare
- Example: 1 day

## Recommended

- Edge TTL = 1 month
- Browser TTL = 1 day

## Key Difference

Edge TTL controls how long Cloudflare keeps the file.
Browser TTL controls how long the visitor’s browser keeps the file.
