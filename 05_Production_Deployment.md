# Production Deployment (React + Node.js)

## Interview Question

Can you explain one production deployment you handled from start to finish?

---

# Answer

Yes.

One of the production deployments I handled involved deploying both a React frontend and a Node.js backend application on a Linux VPS.

The deployment process followed these steps:

### Step 1 - Receive the Latest Code

The development team pushes the latest code to the GitHub repository.

I first verify that the required branch contains the latest changes.

---

### Step 2 - Connect to the Server

I connect to the Linux production server using SSH.

```bash
ssh administrator@server-ip
```

---

### Step 3 - Pull the Latest Code

Navigate to the project directory.

```bash
cd /var/www/project-name
```

Pull the latest changes.

```bash
git pull origin main
```

---

### Step 4 - Deploy the Frontend (React)

Install dependencies.

```bash
npm install
```

Generate the production build.

```bash
npm run build
```

Verify that the build folder is created successfully.

---

### Step 5 - Configure Nginx

Configure Nginx to serve the React build.

Example:

```nginx
server {

    listen 80;

    server_name example.com;

    root /var/www/project/dist;

    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

}
```

Test the configuration.

```bash
sudo nginx -t
```

Restart Nginx.

```bash
sudo systemctl restart nginx
```

---

### Step 6 - Deploy Backend (Node.js)

Navigate to backend directory.

```bash
cd backend
```

Install dependencies.

```bash
npm install
```

Configure environment variables if required.

Start the application using PM2.

```bash
pm2 restart ecosystem.config.js
```

or

```bash
pm2 restart app
```

Verify PM2 status.

```bash
pm2 status
```

---

### Step 7 - Configure Domain

If required,

Configure DNS records in Cloudflare.

Verify

- A Record
- CNAME
- Proxy Status

---

### Step 8 - Configure SSL

Generate SSL certificate using Certbot.

```bash
sudo certbot --nginx
```

Verify HTTPS is working.

---

### Step 9 - Validate Deployment

After deployment I verify:

- Website loads successfully
- HTTPS works correctly
- Login functionality
- APIs are responding
- Images load correctly
- Browser console has no errors

---

### Step 10 - Handover

After successful verification,

I share the production URL with the development team or client and monitor the website for a few minutes to ensure everything is working correctly.

---

# Deployment Workflow

Developer

↓

GitHub Repository

↓

SSH into Linux Server

↓

Git Pull

↓

Install Dependencies

↓

Build React Application

↓

Configure Nginx

↓

Deploy Backend

↓

Start PM2

↓

Configure Cloudflare DNS

↓

Generate SSL (Certbot)

↓

Restart Nginx

↓

Validate Website

↓

Production Live

---

# Commands Used

```bash
ssh

git pull

npm install

npm run build

pm2 restart

pm2 status

pm2 logs

nginx -t

systemctl restart nginx

systemctl status nginx

certbot --nginx

curl

journalctl

tail -f
```

---

# Common Interview Questions

### Why do you use Nginx?

Nginx acts as a reverse proxy and serves static files efficiently. It also forwards API requests to the backend application.

---

### Why do you use PM2?

PM2 keeps the Node.js application running continuously, automatically restarts it if it crashes, and provides process monitoring and logs.

---

### Why Cloudflare?

Cloudflare provides DNS management, SSL support, CDN, caching, and protection against malicious traffic.

---

### Why Certbot?

Certbot automates SSL certificate generation and renewal using Let's Encrypt, enabling secure HTTPS communication.

---

# Real Production Challenges

During deployments I have encountered issues such as:

- Nginx configuration errors
- SSL certificate issues
- Cloudflare DNS propagation delays
- PM2 process failures
- API routing problems
- Environment variable misconfigurations

I troubleshoot these issues by checking logs, validating configurations, and testing the application before making it live.

---

# Interview Tips

✅ Explain the deployment step by step.

✅ Mention commands only after explaining the process.

✅ Speak based on your real experience.

✅ Never skip the validation step.

✅ Mention production issues you solved during deployment.
