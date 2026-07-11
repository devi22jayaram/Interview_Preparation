# Daily Activities as a DevOps Engineer

## Question

Walk me through your daily activities.

---

## Answer

My day usually starts by checking whether all production websites are running properly.

I verify website availability by accessing the URLs and ensure there are no downtime issues.

If there are any issues, I check the Linux server, review Nginx and PM2 status, and analyze logs to identify the root cause.

When developers provide new code, I pull the latest changes from GitHub, deploy the frontend and backend applications, and verify the deployment.

For React applications, I build the project and configure Nginx to serve the static files.

For Node.js applications, I install dependencies, configure environment variables if required, and manage the application using PM2.

I also manage Cloudflare DNS records, configure SSL certificates using Let's Encrypt (Certbot), and ensure websites are accessible over HTTPS.

After deployment, I validate all application functionalities, check API responses, and confirm the website is working as expected before informing the development team or client.

Throughout the day, I troubleshoot production issues related to Linux, Nginx, DNS, SSL, Cloudflare, and application deployments.

---

## Commands I Frequently Use

```bash
ssh
git pull
npm install
npm run build
pm2 restart
pm2 logs
pm2 status
nginx -t
systemctl restart nginx
journalctl
tail -f
curl
df -h
free -h
top
```

---

## Possible Follow-up Questions

- How do you verify website health?
- How do you troubleshoot a deployment issue?
- Why do you use PM2?
- How do you restart Nginx?
- How do you verify SSL?
- How do you monitor Linux servers?

---

## Interview Tips

- Explain your actual work.
- Mention technologies you have used.
- Don't exaggerate.
- Speak confidently.
