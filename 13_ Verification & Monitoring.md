# Step 6 - Verification & Monitoring

Purpose:
Verify Cloudflare caching and bot protection are working correctly.

Checks:
1. F12 → Network → Verify `cf-cache-status: HIT`
2. Cloudflare Analytics → Check Cached Requests
3. Security Analytics → Check Challenged/Blocked Bots
4. Monitor server bandwidth using vnStat

Expected Result:
- More cache hits
- Fewer origin requests
- Reduced bandwidth usage
- Improved website performance
