# ☁️ Cloud Computing & AWS Basics – Structured Notes

---

## 1. What is Cloud Computing?
Cloud computing is the delivery of IT resources (servers, storage, databases, networking, and software) over the internet instead of owning physical hardware.  

- **Pay-as-you-go** model.  
- Examples: AWS, Azure, Google Cloud.  

```
On-Premises (Old Way)          Cloud (New Way)
+-----------+                 +-------------------+
| Servers   |                 | Rent from AWS/Azure|
| Storage   |   ----->        | Pay as you go      |
| Network   |                 | Scalable, flexible |
+-----------+                 +-------------------+
```

---

## 2. Cloud Deployment Models
**Where the cloud is hosted / who owns it**

- **Public Cloud** → Shared by many users (AWS, Azure).  
- **Private Cloud** → Dedicated to one org.  
- **Hybrid Cloud** → Mix of both.  
- **Community Cloud** → Shared by specific groups.  

---

## 3. Cloud Service Models
**What kind of service you get**

- **IaaS (Infrastructure):** Rent servers/storage (EC2, S3).  
- **PaaS (Platform):** Run apps without managing infra (Elastic Beanstalk).  
- **SaaS (Software):** Ready-made apps (Gmail, Salesforce).  

---

## 4. Hypervisor
A **hypervisor** allows multiple VMs on one physical server.  

- **Type 1:** Runs on bare-metal.  
- **Type 2:** Runs on a host OS.  

---

## 5. Amazon EC2
EC2 = AWS virtual servers you can rent.  

- Choose **instance type** (CPU, RAM, Storage).  
- Scalable and pay-per-use.  

Examples:  
- `t2.micro` → Free tier, small apps.  
- `m5.large` → Medium workloads.  
- `p3.2xlarge` → ML/AI workloads with GPU.  

---

## 6. Amazon Machine Image (AMI)
AMI = Template for launching EC2 instances.  

- Includes OS + Apps + Config.  
- Types: AWS AMI, Marketplace AMI, Custom AMI.  

---

## 7. Key Pair
Used for **secure login** to EC2.  

- **Public Key** → Stored in AWS.  
- **Private Key (.pem)** → Downloaded by you.  

---

## 8. Logs
Logs = Files that record events.  

- System Logs → OS-level.  
- Application Logs → Errors, requests.  
- Security Logs → Login attempts.  
- Managed in AWS using **CloudWatch Logs**.  

---

## ✅ Quick Interview One-liners
- **Cloud Computing:** Using IT resources via internet, pay-as-you-go.  
- **Deployment Models:** Public, Private, Hybrid, Community.  
- **Service Models:** IaaS, PaaS, SaaS.  
- **Hypervisor:** Runs multiple VMs on one server.  
- **EC2:** Virtual server on AWS.  
- **AMI:** Template to launch EC2.  
- **Key Pair:** Authentication for EC2 access.  
- **Log:** Record of system/application events.  

---

## 🎯 Common Interview Questions

**Q1. Difference between IaaS, PaaS, SaaS?**  
- IaaS → Infra only (EC2).  
- PaaS → Platform + runtime (Elastic Beanstalk).  
- SaaS → Complete app (Gmail).  

**Q2. What is an AMI?**  
- Template with OS, software, and config used to launch EC2.  

**Q3. What if you lose your EC2 Key Pair private key?**  
- Cannot directly log in.  
- Fix by creating a new key pair & attaching the volume to another instance.  

**Q4. Security Group vs Key Pair?**  
- Key Pair → Authentication (who can log in).  
- Security Group → Firewall (who can connect).  

---

## 🚀 Real-World AWS Use Case: Deploying a Website

Let’s connect everything with a **simple website deployment** example.  

1. **Choose EC2 instance**  
   - Example: `t2.micro` (Free tier, small app).  

2. **Select AMI**  
   - Example: Ubuntu 22.04 AMI.  

3. **Create Key Pair**  
   - Download `.pem` file to securely SSH into instance.  

4. **Configure Security Group**  
   - Allow port **22 (SSH)** → for admin login.  
   - Allow port **80 (HTTP)** → for website traffic.  

5. **Launch EC2 Instance**  
   - Boots up as a virtual server with chosen AMI.  

6. **Install Web Server (inside EC2)**  
   ```bash
   sudo apt update
   sudo apt install apache2 -y
   echo "Hello from AWS EC2!" | sudo tee /var/www/html/index.html
   ```

7. **Access Website**  
   - Open `http://<Public-IP-of-EC2>` in browser.  
   - Website hosted from your EC2! 🎉  

```
Workflow:
User Browser → Internet → AWS EC2 (Apache Web Server) → Response (HTML Page)
```

---

## 🎓 Final Tip
- Always link **concepts to use cases** in interviews.  
  Example: “EC2 + AMI + Key Pair + Security Group + Logs = a complete website deployment.”  

---

# 🌐 Cloud → EC2 → Website Deployment Roadmap

```mermaid
flowchart TD

A[☁️ Cloud Computing Basics] --> B[Cloud Models]
B --> B1[Deployment Models: Public, Private, Hybrid]
B --> B2[Service Models: IaaS, PaaS, SaaS]

B --> C[⚙️ AWS EC2 Basics]
C --> C1[Instance Types (t2.micro, m5.large, etc.)]
C --> C2[AMI (OS + Software Template)]
C --> C3[Key Pair (SSH login)]
C --> C4[Security Group (Firewall rules)]

C --> D[🚀 Launch EC2 Instance]
D --> D1[Select Instance Type]
D --> D2[Choose AMI]
D --> D3[Attach Key Pair]
D --> D4[Configure Security Group]

D --> E[🖥️ Connect to EC2]
E --> F[Install Web Server (Apache/Nginx)]
F --> G[Deploy Website Files]

G --> H[🌍 Website Accessible via Public IP]
```
