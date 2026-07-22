# Get Cloudflare IP Ranges

## Official URL

https://www.cloudflare.com/ips/

## Fetch IPv4

curl https://www.cloudflare.com/ips-v4

## Fetch IPv6

curl https://www.cloudflare.com/ips-v6

## Generate Nginx allow file

sudo mkdir -p /etc/nginx/cloudflare

curl https://www.cloudflare.com/ips-v4 | sed 's/^/allow /; s/$/;/' | sudo tee /etc/nginx/cloudflare/allow.conf

echo 'deny all;' | sudo tee -a /etc/nginx/cloudflare/allow.conf

## Include in Nginx

include /etc/nginx/cloudflare/allow.conf;

## Reload

sudo nginx -t
sudo systemctl reload nginx

## Verify

curl -I https://yourdomain.com
curl -I http://YOUR_SERVER_IP

Expected:
- Domain → 200
- Direct IP → 403 Forbidden
