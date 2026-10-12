# 🚀 Hosting 5 Websites on a Single AWS EC2 Instance Using Nginx

![AWS](https://img.shields.io/badge/AWS-EC2-orange?logo=amazonaws)
![Web Server](https://img.shields.io/badge/Web%20Server-Nginx-green?logo=nginx)
![OS](https://img.shields.io/badge/OS-Amazon%20Linux-blue?logo=linux)
![Project](https://img.shields.io/badge/Project-Hands--On-success)

## 📌 Project Overview

This hands-on cloud project demonstrates how to host **five different websites on a single AWS EC2 instance** using the Nginx web server.

Each website uses a separate document root and port number, allowing multiple websites to run independently on one Linux server.

## 🎯 Project Objectives

- ☁️ Launch and configure an AWS EC2 instance.
- 🐧 Install and manage Nginx on Amazon Linux.
- 🌐 Host five separate HTML websites.
- 🔌 Configure multiple ports using Nginx server blocks.
- 🔐 Configure AWS Security Group inbound rules.
- 🛠️ Practice Linux commands and troubleshooting.

## 🏗️ Architecture

**User Browser → AWS EC2 Instance → Nginx → Website Content**

Nginx listens on five ports and serves the corresponding website files from separate directories.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| AWS EC2 | Cloud virtual server |
| Amazon Linux | Server operating system |
| Nginx | Web server |
| HTML | Website content |
| Linux | Server administration |
| AWS Security Groups | Network access control |

## 🌐 Website Details

| Website | Port | Document Root |
|---|---:|---|
| Cloud Engineer | 80 | `/var/www/site1` |
| DevOps Engineering | 8080 | `/var/www/site2` |
| Linux Server Administration | 8081 | `/var/www/site3` |
| AWS Cloud Services | 9090 | `/var/www/site4` |
| Docker & Containers | 9091 | `/var/www/site5` |

## ⚙️ Implementation Steps

### 1. Update the server

```bash
sudo yum update -y
```

### 2. Install Nginx

```bash
sudo yum install nginx -y
```

### 3. Create website directories

```bash
sudo mkdir -p /var/www/site{1,2,3,4,5}
```

### 4. Create HTML files

```bash
sudo touch /var/www/site1/index.html
sudo touch /var/www/site2/index.html
sudo touch /var/www/site3/index.html
sudo touch /var/www/site4/index.html
sudo touch /var/www/site5/index.html
```

Add different HTML content to each `index.html` file.

### 5. Configure Nginx

Create the configuration file:

```bash
sudo vi /etc/nginx/conf.d/websites.conf
```

Add the following configuration:

```nginx
server {
    listen 80;
    server_name _;
    root /var/www/site1;
    index index.html;
}

server {
    listen 8080;
    server_name _;
    root /var/www/site2;
    index index.html;
}

server {
    listen 8081;
    server_name _;
    root /var/www/site3;
    index index.html;
}

server {
    listen 9090;
    server_name _;
    root /var/www/site4;
    index index.html;
}

server {
    listen 9091;
    server_name _;
    root /var/www/site5;
    index index.html;
}
```

### 6. Configure AWS Security Group

Allow the required inbound ports for this practice project:

- `22` — SSH administration
- `80` — Website 1
- `8080` — Website 2
- `8081` — Website 3
- `9090` — Website 4
- `9091` — Website 5

**Security note:** Restrict SSH access to your own IP. Public website ports should be exposed only as needed.

### 7. Test the Nginx configuration

```bash
sudo nginx -t
```

### 8. Start and enable Nginx

```bash
sudo systemctl enable --now nginx
sudo systemctl restart nginx
```

### 9. Verify listening ports

```bash
sudo ss -ltnp | grep nginx
```

## ✅ Expected Results

After replacing `EC2_PUBLIC_IP` with your instance's current public IPv4 address, open:

- `http://EC2_PUBLIC_IP` — Cloud Engineer
- `http://EC2_PUBLIC_IP:8080` — DevOps Engineering
- `http://EC2_PUBLIC_IP:8081` — Linux Server Administration
- `http://EC2_PUBLIC_IP:9090` — AWS Cloud Services
- `http://EC2_PUBLIC_IP:9091` — Docker & Containers

Each URL should display its corresponding website.

## 🧠 Key Learnings

- AWS EC2 instance configuration
- Nginx server blocks and port-based website hosting
- Linux file and directory management
- Security Group and inbound port configuration
- Nginx configuration testing and service management
- Troubleshooting website connectivity issues

## 🔮 Future Improvements

- 🌍 Configure custom domains using Amazon Route 53.
- 🔒 Enable HTTPS using SSL/TLS certificates.
- ⚖️ Explore an Application Load Balancer.
- 🔄 Automate deployment using CI/CD tools such as Jenkins.

## 👨‍💻 Author

**Mohit Gadilohar**

Aspiring Cloud & DevOps Engineer | AWS | Linux | Docker | CI/CD

🔗 [Connect with me on LinkedIn](https://www.linkedin.com/in/mohit-gadilohar-devops)

---

⭐ If you find this project useful, consider starring the repository!

**#AWS #EC2 #Nginx #Linux #CloudComputing #DevOps**
