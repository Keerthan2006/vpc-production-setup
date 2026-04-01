# 📘 AWS Highly Available VPC Architecture with ALB & Auto Scaling
---
Architecture Overview: https://docs.aws.amazon.com/images/vpc/latest/userguide/images/vpc-example-private-subnets.png
---

---
Video Demo: https://drive.google.com/file/d/12HCxhAJ-WhcTyuRLWTwQqoLrf1ps3I8n/view?usp=sharing
---

## 📌 Project Overview

This project demonstrates the design and implementation of a **highly available and secure AWS infrastructure** using:

- Multi-AZ VPC architecture  
- Public and Private Subnets  
- NAT Gateways  
- Bastion Host  
- Auto Scaling Group  
- Application Load Balancer  

The goal is to deploy a scalable web application in **private subnets** while ensuring **secure access and high availability**.

---

## 🏗️ Architecture Summary

- 2 Availability Zones (AZs)
- Each AZ contains:
  - 1 Public Subnet
  - 1 Private Subnet

### Public Subnets:
- Application Load Balancer (ALB)
- NAT Gateway
- Bastion Host

### Private Subnets:
- EC2 instances running application (Port 8000)

---

## 🔁 Traffic Flow
User → Application Load Balancer → Target Group → EC2 (Private Subnet)
                                           ↓
                                   NAT Gateway (Outbound Internet)


---

## 🧩 Components Used

### 🌐 VPC
- Custom VPC with CIDR block
- Designed across 2 AZs for high availability

### 🛣️ Subnets
- Public Subnets → Internet-facing resources  
- Private Subnets → Secure application layer  

### 🌍 Internet Gateway
- Allows communication between VPC and Internet

### 🔁 NAT Gateway
- Deployed in each public subnet
- Enables outbound internet access for private instances

### 🛡️ Security Groups
- Allowed inbound:
  - Port 22 (SSH)
  - Port 80 (HTTP)
  - Port 8000 (Application)
- Source: 0.0.0.0/0

### 💻 Bastion Host
- Placed in public subnet
- Used to securely SSH into private EC2 instances

### ⚙️ Auto Scaling Group (ASG)
- Desired Capacity: 2
- Maximum Capacity: 4
- Instances distributed across private subnets in multiple AZs

### ⚖️ Application Load Balancer (ALB)
- Internet-facing
- Routes traffic to target group
- Performs health checks

### 🎯 Target Group
- Registered private EC2 instances
- Routes traffic on port 8000

---

## 🚀 Deployment Steps

1. Created VPC with 2 Availability Zones  
2. Created Public and Private Subnets in each AZ  
3. Attached Internet Gateway to VPC  
4. Created 2 NAT Gateways (one per AZ)  
5. Configured Route Tables for public and private subnets  
6. Created Security Group allowing ports 22, 80, 8000  
7. Launched Bastion Host in public subnet  
8. Created Launch Template for EC2 instances  
9. Created Auto Scaling Group in private subnets  
10. Deployed application on port 8000 in EC2 instances  
11. Created Target Group and registered instances  
12. Created Application Load Balancer in public subnets  
13. Connected ALB to Target Group  
14. Accessed application using ALB DNS  

---

## 🔐 Key Features

- High Availability (Multi-AZ deployment)
- Secure Architecture (Private Subnets + Bastion)
- Scalability (Auto Scaling Group)
- Load Distribution (Application Load Balancer)
- Fault Tolerance

---
---
---

## 🧠 What I Learned

- Designing highly available AWS architectures  
- Securing infrastructure using private subnets  
- Load balancing and scaling applications  
- Managing EC2 access via Bastion Host  
- Real-world DevOps architecture implementation  

---

## 👨‍💻 Author

**Keerthan**  
B.Tech 3rd Year | Cloud & DevOps Enthusiast
