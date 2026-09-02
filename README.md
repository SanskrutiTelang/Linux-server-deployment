# Linux Server Deployment on AWS

## 📌 Project Overview

This project demonstrates how to create, configure, secure, and deploy a Linux server using AWS EC2.

The server runs Ubuntu Server and hosts a simple website using Nginx.

## 🏗️ Architecture

```text
                    Internet
                       |
                       v
                AWS Security Group
                       |
                 Port 22 / Port 80
                       |
                       v
                Ubuntu EC2 Server
                       |
                    UFW Firewall
                       |
                       v
                     Nginx
                       |
                       v
                   index.html
```

## 🛠️ Technologies Used

* AWS EC2
* Ubuntu Server
* Linux CLI
* SSH
* SSH Keys
* UFW Firewall
* Nginx
* HTTP
* Git
* GitHub

## 🚀 Deployment Steps

### 1. Create EC2 Instance

Created an AWS EC2 instance using Ubuntu Server 24.04 LTS.

Configured the security group with:

| Protocol | Port | Source   | Purpose              |
| -------- | ---: | -------- | -------------------- |
| SSH      |   22 | My IP    | Secure server access |
| HTTP     |   80 | Anywhere | Web access           |

### 2. Connect to the Server

Connected to the Ubuntu server using SSH:

```bash
ssh -i linux-lab-key.pem ubuntu@SERVER_IP
```

The private SSH key was kept locally and was NOT uploaded to GitHub.

### 3. Configure Linux

Updated the system:

```bash
sudo apt update
sudo apt upgrade -y
```

Created an additional Linux user:

```bash
sudo adduser devuser
sudo usermod -aG sudo devuser
```

### 4. File Permissions

Created test files and practiced Linux permissions:

```bash
touch test.txt
ls -l
chmod +x hello.sh
```

Also practiced ownership using:

```bash
chown
chgrp
```

### 5. Configure Firewall

Configured UFW:

```bash
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw enable
```

Verified the firewall:

```bash
sudo ufw status
```

### 6. Install Nginx

Installed Nginx:

```bash
sudo apt install nginx -y
```

Started the service:

```bash
sudo systemctl start nginx
```

Enabled it at boot:

```bash
sudo systemctl enable nginx
```

Checked the service:

```bash
sudo systemctl status nginx
```

### 7. Deploy Website

Created the website at:

```text
/var/www/html/index.html
```

Tested it locally:

```bash
curl http://localhost
```

### 8. Test Connectivity

Tested the server from my computer using:

```bash
curl http://SERVER_IP
```

The website was also accessed through:

```text
http://SERVER_IP
```

## 🔐 Security

The following security practices were used:

* SSH access through port 22
* SSH restricted to my IP address through the AWS security group
* UFW firewall configured
* HTTP exposed only through port 80
* SSH private key kept outside the repository
* No passwords, private keys, or AWS credentials committed to GitHub

## 📸 Screenshots

Screenshots showing the deployment process are available in the `screenshots` directory.

## 📚 Linux Commands Practiced

### File Management

```bash
pwd
ls
cd
mkdir
touch
cp
mv
rm
cat
```

### Permissions

```bash
chmod
chown
chgrp
ls -l
```

### Users and Groups

```bash
whoami
adduser
usermod
groups
```

### Processes

```bash
ps
top
kill
```

### Services

```bash
systemctl status
systemctl start
systemctl stop
systemctl restart
systemctl enable
```

### Networking

```bash
ip addr
ip route
ss
curl
ping
```

### Firewall

```bash
ufw status
ufw allow
ufw enable
```

## 🎯 What I Learned

Through this project I learned how to:

* Create a Linux server using AWS EC2
* Connect to Linux using SSH
* Manage Linux files and directories
* Manage users and groups
* Configure file permissions
* Manage processes and services
* Configure a firewall
* Understand IP addresses and ports
* Deploy an Nginx web server
* Test network connectivity
* Document a server deployment using GitHub

## 🏁 Result

Successfully deployed a website on an Ubuntu Linux server using AWS EC2 and Nginx.

The EC2 instance can be terminated after the lab while the project documentation remains available in this GitHub repository.
