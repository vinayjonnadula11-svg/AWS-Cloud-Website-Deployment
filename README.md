# ☁️ AWS Cloud Website Deployment

## 📌 Project Overview

This project demonstrates the deployment of a **static website on Amazon Web Services (AWS)** using EC2, Application Load Balancer, and Auto Scaling.

A custom VPC was created with public and private subnets across two Availability Zones. Two EC2 instances were deployed in private subnets and configured with Nginx to host the website.

An internet-facing Application Load Balancer distributes incoming traffic between the EC2 instances, while an Auto Scaling Group maintains the desired instance capacity.

## 🎯 Project Objectives

- Deploy a static website on AWS.
- Create a custom VPC with public and private subnets.
- Configure EC2 instances across multiple Availability Zones.
- Implement Application Load Balancing.
- Configure Auto Scaling for high availability.
- Host website files using Nginx.
- Manage website source code using GitHub.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| AWS VPC | Cloud network configuration |
| Amazon EC2 | Website hosting servers |
| Application Load Balancer | Distributing incoming traffic |
| Auto Scaling Group | Maintaining EC2 capacity |
| Target Group | Registering and monitoring instances |
| IAM | Secure instance access |
| Amazon Linux 2023 | Operating system |
| Nginx | Web server |
| HTML, CSS, JavaScript | Website development |
| Git & GitHub | Source code management |

## 🏗️ AWS Architecture

The project uses a custom VPC with two Availability Zones.

```text
                 User / Browser
                       |
                       |
             Application Load Balancer
                       |
                 Target Group
                  /        \
                 /          \
          EC2 Instance 1   EC2 Instance 2
             (Private)       (Private)
                 |               |
              Nginx           Nginx
                 |               |
             Website         Website

           Auto Scaling Group
          Desired Capacity: 2
```

## 🔄 Project Implementation Workflow

### 1. VPC Configuration

- Created a custom VPC named `three-tier-vpc`.
- Configured two public and two private subnets.
- Created Internet Gateway and NAT Gateway.
- Configured public and private route tables.

### 2. Security Group Configuration

- Created `alb-sg` to allow public HTTP traffic on port 80.
- Created `web-ec2-sg` to allow HTTP traffic only from the ALB Security Group.
- Restricted direct public access to EC2 instances.

### 3. EC2 and Launch Template

- Created an IAM role with Systems Manager access.
- Created a Launch Template named `web-server-template`.
- Selected Amazon Linux 2023.
- Configured Nginx installation using User Data.

### 4. Target Group Configuration

- Created `web-target-group`.
- Configured HTTP on port 80.
- Set the health check path to `/`.
- Registered EC2 instances for health monitoring.

### 5. Application Load Balancer

- Created an internet-facing ALB named `web-application-alb`.
- Configured it in two public subnets.
- Added an HTTP listener on port 80.
- Forwarded incoming traffic to the Target Group.

### 6. Auto Scaling Configuration

- Created `web-auto-scaling-group`.
- Configured two private subnets across different Availability Zones.
- Set desired capacity to 2.
- Set minimum capacity to 2 and maximum capacity to 3.
- Attached the Target Group.

### 7. Website Deployment

- Developed the website using HTML, CSS and JavaScript.
- Uploaded the source code to GitHub.
- Connected to both EC2 instances using Systems Manager Session Manager.
- Cloned the GitHub repository.
- Copied website files into `/usr/share/nginx/html/`.
- Restarted Nginx on both instances.

### 8. Website Access

Accessed the deployed website through the Application Load Balancer DNS URL.

**Live Website:** http://web-application-alb-1870557470.ap-south-1.elb.amazonaws.com/

## 📸 Project Screenshots

### 🌐 1. VPC Architecture

Shows the custom VPC with public and private subnets, Internet Gateway and NAT Gateway.

<img width="1560" height="435" alt="Screenshot 2026-11-17 180238" src="https://github.com/user-attachments/assets/d8284fc1-88bd-4989-8be8-5905254b9626" />


### 💻 2. EC2 Instances

Shows both EC2 instances running in private subnets across two Availability Zones.

<img width="1241" height="140" alt="image" src="https://github.com/user-attachments/assets/17a498d3-7575-4f6e-9ec4-736ed5faca48" />


### ⚙️ 3. Target Group

Shows the registered EC2 instances and their health status.

<img width="1530" height="332" alt="Screenshot 2026-11-17 180446" src="https://github.com/user-attachments/assets/da5c020a-6cc1-4dc3-9f79-7f4e753a4746" />


### 🚀 4. Final Website Output

Shows the successfully deployed website accessed through the Application Load Balancer DNS URL.

<img width="1822" height="973" alt="Screenshot 2026-11-17 183639" src="https://github.com/user-attachments/assets/3f2e626a-506c-4432-9c7b-60deafe6a9de" />


## ✨ Key Features

- Custom AWS VPC architecture.
- Public and private subnet configuration.
- EC2 instances deployed across two Availability Zones.
- Internet-facing Application Load Balancer.
- Target Group health checks.
- Auto Scaling configuration.
- Private EC2 access using Session Manager.
- Nginx-based static website hosting.
- GitHub-based source code management.

## 📚 Learning Outcomes

Through this project, I gained practical knowledge of:

- AWS cloud infrastructure.
- VPC and subnet configuration.
- EC2 instance management.
- Load balancing and Auto Scaling.
- IAM roles and Security Groups.
- Linux administration.
- Nginx web server configuration.
- Git and GitHub.
- Static website deployment.

## 👨‍💻 Project Information

| Category | Details |
|---|---|
| Project Name | AWS Cloud Website Deployment |
| Project Type | Cloud Computing |
| Cloud Platform | Amazon Web Services |
| Web Server | Nginx |
| Deployment | EC2 with Application Load Balancer |
| Architecture | Multi-AZ |
| Application | Static Website |

## 🙌 Conclusion

Successfully deployed a publicly accessible static website on AWS using EC2, Application Load Balancer, Auto Scaling, and Nginx.

This project provided hands-on experience in cloud networking, website hosting, traffic distribution, and highly available infrastructure.

**Developed as a practical AWS Cloud Computing Project.**
