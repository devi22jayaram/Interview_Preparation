# Daily Activities - Follow-up Interview Questions

---

# 1. How do you verify website health?

## Answer

Whenever I start my day or complete a deployment, I verify that the website is healthy by following a structured approach.

1. I first open the website in a browser and verify that all pages load correctly.
2. I check whether both HTTP and HTTPS are working properly.
3. I verify that the frontend can communicate with the backend APIs.
4. I ensure the backend application is running using PM2.
5. I verify that Nginx is running correctly.
6. I check the application logs if I notice any issues.
7. If required, I use curl to verify API responses.

This process helps me confirm that the application is available and functioning correctly before informing the team or client.

### Commands

```bash
pm2 status
systemctl status nginx
curl https://example.com
curl https://api.example.com
```

---

# 2. How do you troubleshoot a deployment issue?

## Answer

Whenever a deployment issue occurs, I follow a step-by-step troubleshooting approach instead of making assumptions.

1. Verify whether the application is running.
2. Check PM2 status.
3. Verify the Nginx configuration using `nginx -t`.
4. Review Nginx and application logs.
5. Check DNS records in Cloudflare.
6. Verify SSL certificate status.
7. Restart the required services if necessary.
8. Validate the application after fixing the issue.

Following a structured process helps identify the root cause quickly.

### Commands

```bash
pm2 logs
pm2 status
nginx -t
systemctl restart nginx
journalctl -u nginx
tail -f /var/log/nginx/error.log
```

---

# 3. Why do you use PM2?

## Answer

PM2 is a process manager for Node.js applications.

I use PM2 because it:

- Keeps the application running continuously.
- Automatically restarts the application if it crashes.
- Allows zero-downtime restarts.
- Provides application logs.
- Makes it easy to monitor running applications.

Using PM2 improves application reliability in production.

### Commands

```bash
pm2 start app.js
pm2 restart app
pm2 stop app
pm2 delete app
pm2 logs
pm2 status
```

---

# 4. How do you restart Nginx?

## Answer

Before restarting Nginx, I always validate the configuration.

If the configuration is correct, I restart the Nginx service.

This helps avoid downtime caused by configuration errors.

### Commands

```bash
sudo nginx -t
sudo systemctl restart nginx
sudo systemctl status nginx
```

---

# 5. How do you verify SSL?

## Answer

After configuring SSL, I verify it using multiple methods.

1. Open the website in a browser and confirm the HTTPS lock icon.
2. Check that the SSL certificate is valid and not expired.
3. Verify certificate details using OpenSSL if required.
4. Test the website using curl.

This ensures secure communication between users and the server.

### Commands

```bash
curl -I https://example.com

openssl s_client -connect example.com:443
```

---

# 6. How do you monitor Linux servers?

## Answer

I monitor Linux servers by checking system resources and service status.

I regularly monitor:

- CPU utilization
- Memory usage
- Disk usage
- Running processes
- Nginx service
- PM2 processes
- Application logs

This helps detect issues before they affect users.

### Commands

```bash
top
htop
free -h
df -h
du -sh
ps -ef
systemctl status nginx
pm2 status
journalctl
```

---

# Interview Tips

✔ Explain the steps in sequence.

✔ Mention commands only after explaining the process.

✔ Emphasize troubleshooting methodology.

✔ Speak confidently and relate your answers to your real production experience.
