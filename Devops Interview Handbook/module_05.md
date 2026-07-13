# 📘 DevOps Interview Handbook
# Module 05: Computer Networking for DevOps Engineers

> **Target Audience:** DevOps Engineers (1–2 Years Experience)
>
> **Goal:** Understand networking concepts required for Linux servers, cloud platforms, web applications, and production troubleshooting.

---

# Table of Contents

1. Introduction to Networking
2. Network Types
3. OSI Model
4. TCP/IP Model
5. IP Address
6. Public vs Private IP
7. IPv4 vs IPv6
8. Subnet Mask
9. Gateway
10. MAC Address
11. Ports
12. TCP vs UDP
13. DNS
14. HTTP & HTTPS
15. SSL/TLS
16. SSH
17. NAT
18. CIDR
19. Important Networking Commands
20. Production Troubleshooting
21. Common Interview Questions
22. Interview Tips

---

# 1. What is Networking?

## Definition

Networking is the communication between two or more devices to exchange data using standard protocols.

Example

```
Laptop
      │
Internet
      │
Web Server
      │
Database Server
```

As a DevOps Engineer, networking is essential for deploying applications, configuring servers, troubleshooting connectivity issues, and managing cloud infrastructure.

---

# 2. Types of Networks

### LAN (Local Area Network)

- Office Network
- Home Network

Example

```
Laptop
Printer
Server
```

---

### WAN (Wide Area Network)

Connects multiple LANs over long distances.

Example

Internet

---

### MAN

Metropolitan Area Network

Used inside a city.

---

# 3. OSI Model

There are **7 Layers**.

```
7. Application
6. Presentation
5. Session
4. Transport
3. Network
2. Data Link
1. Physical
```

---

## Easy Trick

```
All
People
Seem
To
Need
Data
Processing
```

---

## Important Layers

### Layer 7

HTTP

HTTPS

FTP

SSH

SMTP

---

### Layer 4

TCP

UDP

---

### Layer 3

IP Address

Routing

---

### Layer 2

MAC Address

---

### Layer 1

Cable

Fiber

Switch

---

# Interview Tip

Most companies ask only Layer 3 and Layer 4.

---

# 4. TCP/IP Model

```
Application

Transport

Internet

Network Access
```

Used in real-world networking.

---

# 5. IP Address

Definition

Unique address assigned to every device.

Example

```
192.168.1.10
```

Without IP Address,

devices cannot communicate.

---

# 6. Public IP vs Private IP

## Public IP

Accessible over Internet.

Example

AWS EC2 Public IP

---

## Private IP

Accessible only inside internal network.

Examples

```
192.168.x.x

172.16.x.x

10.x.x.x
```

---

# Interview Answer

> Public IP is used for communication over the Internet, while Private IP is used for internal communication within a network. In AWS, EC2 instances often have both private and public IP addresses.

---

# 7. IPv4 vs IPv6

IPv4

```
192.168.1.1
```

32-bit

---

IPv6

```
2001:db8::1
```

128-bit

Supports significantly more addresses.

---

# 8. Subnet Mask

Used to divide a network into smaller networks.

Example

```
255.255.255.0
```

CIDR

```
/24
```

---

# 9. Default Gateway

Acts as the exit point from one network to another.

Example

```
Laptop

↓

Router

↓

Internet
```

---

# 10. MAC Address

Physical address of a network interface card (NIC).

Example

```
00:1A:2B:3C:4D:5E
```

Works at Layer 2.

---

# 11. Ports

A port identifies a specific service running on a server.

Common Ports

| Port | Service |
|------|----------|
| 22 | SSH |
| 21 | FTP |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 3306 | MySQL |
| 5432 | PostgreSQL |
| 27017 | MongoDB |

---

# Production Example

Your Node.js app runs on

```
3000
```

Nginx listens on

```
80

443
```

Nginx forwards requests to

```
localhost:3000
```

---

# 12. TCP vs UDP

## TCP

Reliable

Connection-Oriented

Error Checking

Acknowledgement

Examples

- HTTP
- HTTPS
- SSH

---

## UDP

Fast

Connectionless

No Acknowledgement

Examples

- Video Streaming
- Gaming
- DNS Queries

---

## Interview Answer

> TCP guarantees reliable communication using acknowledgements and retransmissions, making it suitable for web applications and SSH. UDP is faster but does not guarantee delivery, making it suitable for streaming and DNS.

---

# 13. DNS

## What is DNS?

DNS converts a domain name into an IP address.

Example

```
google.com

↓

DNS

↓

142.xx.xx.xx
```

---

Production Example

```
www.company.com

↓

Cloudflare DNS

↓

AWS Public IP

↓

Nginx

↓

Node.js
```

---

# 14. HTTP & HTTPS

## HTTP

Port

80

Not encrypted.

---

## HTTPS

Port

443

Encrypted using SSL/TLS.

---

# Interview Answer

> HTTPS is the secure version of HTTP. It encrypts communication using SSL/TLS, protecting data exchanged between clients and servers.

---

# 15. SSL/TLS

Purpose

Encrypts communication.

Provides

- Confidentiality
- Integrity
- Authentication

---

Production Example

```
Let's Encrypt

↓

Certificate

↓

Nginx

↓

HTTPS Enabled
```

---

# 16. SSH

Secure Shell

Used for remote server access.

Example

```bash
ssh ubuntu@192.168.1.100
```

Default Port

```
22
```

---

# 17. NAT

Network Address Translation

Allows private IP addresses to communicate with the Internet through a public IP.

Example

Office Network

↓

Router

↓

Internet

---

# 18. CIDR

Classless Inter-Domain Routing

Example

```
192.168.1.0/24
```

Frequently used in AWS VPC.

---

# 19. Important Networking Commands

Check IP

```bash
ip addr
```

---

Check Routing

```bash
ip route
```

---

Ping

```bash
ping google.com
```

---

DNS Lookup

```bash
nslookup google.com
```

or

```bash
dig google.com
```

---

Open Ports

```bash
ss -tulnp
```

---

Older Command

```bash
netstat -tulnp
```

---

Traceroute

```bash
traceroute google.com
```

---

Download Test

```bash
curl https://example.com
```

---

HTTP Headers

```bash
curl -I https://example.com
```

---

# 20. Production Troubleshooting

## Scenario 1

Website not opening.

Steps

```
Ping Domain

↓

DNS Lookup

↓

Check Server Reachability

↓

Check Nginx

↓

Check Backend

↓

Check Firewall
```

Commands

```bash
ping domain.com

nslookup domain.com

curl -I domain.com

systemctl status nginx

ss -tulnp
```

---

## Scenario 2

DNS not resolving.

Check

```bash
dig domain.com

nslookup domain.com
```

Verify

Cloudflare

GoDaddy

Route53

---

## Scenario 3

Backend not reachable.

Check

```bash
curl localhost:3000

ss -tulnp

pm2 list
```

---

# 21. Common Interview Questions

- What is Networking?
- Explain OSI Model.
- Difference between OSI and TCP/IP.
- What is IP Address?
- Difference between Public and Private IP.
- Difference between IPv4 and IPv6.
- What is Gateway?
- What is MAC Address?
- What is DNS?
- Difference between TCP and UDP.
- Difference between HTTP and HTTPS.
- What is SSL/TLS?
- What is NAT?
- What is CIDR?
- Explain Port Numbers.
- Which command checks open ports?
- Which command checks DNS?

---

# 22. Interview Tips

❌ Don't Say

> DNS converts domain into IP.

✅ Say

> DNS is a distributed naming system that translates human-readable domain names into IP addresses. In my current role, I frequently verify DNS propagation using nslookup or dig while configuring domains in Cloudflare.

---

❌ Don't Say

> HTTP is insecure.

✅ Say

> HTTP transfers data in plain text over port 80, whereas HTTPS uses SSL/TLS encryption over port 443 to ensure secure communication.

---

❌ Don't Say

> TCP is reliable.

✅ Say

> TCP provides reliable, connection-oriented communication using acknowledgements, sequencing, and retransmissions. This makes it suitable for web applications, SSH, and database connections.

---

# Key Takeaways

✔ Every server has an IP address.

✔ DNS converts domain names into IP addresses.

✔ HTTP uses Port 80.

✔ HTTPS uses Port 443.

✔ SSH uses Port 22.

✔ Understand TCP vs UDP.

✔ Learn common networking commands.

✔ Most production issues begin with checking DNS, ports, connectivity, and services.

✔ Always explain concepts using production examples.

---
