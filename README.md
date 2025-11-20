# 🚀 Host Website on AWS EC2 Using NGINX + Domain Mapping + SSL

This guide explains how to:
1. Launch EC2  
2. Install NGINX  
3. Map your domain  
4. Secure it using Let's Encrypt SSL  

---

## ✅ 1️⃣ Launch EC2 Instance
- Go to AWS EC2 Console
- Create Instance → Ubuntu 22.04 → t2.micro
- Open these ports in Security Group:
  - 22 (SSH)
  - 80 (HTTP)
  - 443 (HTTPS)
- Launch & connect using SSH / PuTTY

---

## ✅ 2️⃣ Install & Start NGINX

```bash
sudo apt update -y
sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
```


### Open in browser
```bash
http://YOUR_PUBLIC_IP
```

### Go to route 53 and create a hosted zone
copy paste the NS in DNS setup
create the records

### You should see the NGINX Welcome Page.

✅ 3️⃣ Domain Mapping (DNS Setup)

Go to your Domain Provider (GoDaddy / Namecheap / Hostinger / DomainPlat etc.)

Add these records in DNS:
```bash
Type: A
Name: @
Value: YOUR_PUBLIC_IP

Type: A
Name: www
Value: YOUR_PUBLIC_IP
```

Wait 5–10 minutes.

### Open:
```bash
http://yourdomain.com
```

### Your NGINX page should load with your domain.

### ✅ 4️⃣ Install SSL (HTTPS) Using Certbot

Install Certbot
```bash
sudo apt install certbot python3-certbot-nginx -y
```

### Issue SSL Certificate
```bash
sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
```

During setup:

Enter email

Agree terms

Select “Redirect all traffic to HTTPS”

### Now verify:
``` bash
https://yourdomain.com
```

Your site is now secure with SSL.
Issue SSL Certificate
