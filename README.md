# 🌐 Multi Server Hosting on AWS Linux (Mumbai Region)

## 🚀 Overview

Welcome to the **Multi Server Hosting on AWS** project! This guide demonstrates how to host **multiple websites** on a **single Amazon Linux EC2 instance** using the **Mumbai region** on AWS. By leveraging AWS services, this setup enables an efficient, scalable, and cost-effective solution—ideal for developers and small businesses.

---

## 🔑 Key Features

- ✅ **Single EC2 Instance Hosting** — Host multiple websites on one EC2 instance.
- ✅ **Apache Web Server Setup** — Configure Apache to handle multiple virtual hosts.
- ✅ **Domain & SSL Configuration** — Set up secure domains for each hosted site.
- ✅ **Cost Optimization** — Reduce costs by maximizing server resource utilization.

---

## 📋 Prerequisites

Before you begin, ensure the following:

- An active **AWS Account** ([Sign up here](https://aws.amazon.com/free/))
- Basic understanding of **Linux commands** and **AWS EC2**
- Access to **domain names** for each website you plan to host

---

## 🛠️ Setup Instructions

### Step 1: Launch an EC2 Instance

1. Log in to your **[AWS Management Console](https://console.aws.amazon.com/)**.
2. Navigate to **EC2** and launch a new instance:
   - Choose **Amazon Linux 2 AMI**
   - Select instance type: e.g., `t2.micro` (Free Tier eligible)
   - Configure **Security Group** to allow:
     - `HTTP (port 80)`
     - `HTTPS (port 443)`
     - `SSH (port 22)`
   - Assign an **Elastic IP** to retain a static public IP address.
   - Create or select an existing **SSH key pair** for access.

---

### Step 2: Install Apache Web Server

1. **Connect to EC2 via SSH:**

   ```bash
   ssh -i your-key.pem ec2-user@your-instance-public-ip

2. **Update packages**

   ```bash
   sudo yum update -y

4. **Install Apache**

   ```bash 
   sudo yum install httpd -y

5. **Start Apache and enable it on boot**

   ```bash  
   sudo service httpd start
   sudo chkconfig httpd on
    
# Configure Firewall for Apache
## 1.Allow HTTP and HTTPS traffic in the security group:
- Go to your EC2 Dashboard.
- Click on "Security Groups" in the left menu.
- Select the security group associated with your EC2 instance.
- Under the "Inbound rules" tab, ensure that rules for HTTP (port 80) and HTTPS (port 443) are 
  added.
5. **Create directories for each website**

  ```bash
  sudo mkdir -p /var/www/html/website1
  sudo mkdir -p /var/www/html/website2
