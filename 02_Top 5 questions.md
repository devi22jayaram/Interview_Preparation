1.Can you explain your current role at Wizinoa?
Currently, I am working as a DevOps Engineer at Wizinoa Technologies. My primary responsibility is to manage Linux production servers and support application deployments.

I work with React frontend and Node.js backend applications. My daily tasks include configuring Nginx reverse proxy, managing Cloudflare DNS records, implementing SSL certificates using Let's Encrypt (Certbot), and managing backend services using PM2.

Apart from deployments, I also troubleshoot production issues related to DNS, SSL, Nginx configuration, routing, and server availability. Before handing over a project to the client, I verify that the website is working correctly over both HTTP and HTTPS.

I also collaborate with developers during deployments and help ensure smooth production releases with minimal downtime.


2.What do you like most about your job?
I enjoy troubleshooting production issues because every issue teaches me something new. I also like deploying applications and seeing them go live successfully.

3.Can you explain one production deployment?
One of the deployments I handled was for a client website where both the React frontend and Node.js backend had to be deployed on a Linux VPS.

First, I pulled the latest code from GitHub. For the frontend, I installed the dependencies, generated the production build, and configured Nginx to serve the build files.

For the backend, I configured the environment variables, started the application using PM2, and verified that the API was working correctly.

After that, I configured the domain in Cloudflare, updated the DNS records, generated an SSL certificate using Let's Encrypt (Certbot), enabled HTTPS, and tested the application.

Finally, I verified that the website was accessible, all pages loaded correctly, and the APIs were functioning as expected before sharing the production URL with the team.


4.Walk me through your daily activities.My day usually starts by checking whether all production websites are running properly. If there are any issues, I investigate the logs and resolve them.

When there are new deployments, I pull the latest code, deploy the frontend and backend applications, configure Nginx if required, and manage the backend processes using PM2.

I also handle Cloudflare DNS updates, SSL certificate configuration and renewal, and troubleshoot issues related to routing, DNS, HTTPS, and application availability.

Throughout the day, I coordinate with developers to resolve deployment-related issues and ensure that production services remain stable.


5.How do you deploy a React + Node.js application?

Developer
      │
      ▼
 GitHub Repository
      │
      ▼
Linux Server
      │
 ┌──────────────┐
 │ React Build  │
 └──────────────┘
      │
      ▼
Nginx
      │
      ▼
User
      │
      ▼
Node.js Backend (PM2)
      │
      ▼
MongoDB

First, I connect to the Linux server using SSH and pull the latest code from GitHub.

For the React application, I install the dependencies, generate the production build, and configure Nginx to serve the build directory.

For the Node.js backend, I configure the required environment variables, install dependencies, and start or restart the application using PM2.

Then I configure the Nginx reverse proxy to forward API requests to the backend application.

If the domain is new, I configure the DNS records in Cloudflare, generate an SSL certificate using Let's Encrypt (Certbot), enable HTTPS, and restart Nginx.

Finally, I test the frontend, backend APIs, login functionality, and overall website before confirming that the deployment is successful.



6.Can you explain one production issue you resolved?
One production issue I handled was related to a website that was not loading correctly after deployment.

I first checked whether the backend application was running using PM2. Then I verified the Nginx configuration using `nginx -t` and checked the Nginx error logs.

After investigation, I found that the issue was related to the Nginx configuration and SSL setup. I corrected the configuration, verified the SSL certificate, restarted Nginx, and tested the application using a browser and curl.

Once everything was working correctly, I informed the development team and confirmed with the client that the website was accessible again.

This experience taught me the importance of following a structured troubleshooting process instead of making assumptions.







