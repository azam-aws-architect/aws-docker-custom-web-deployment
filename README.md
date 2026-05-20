# AWS Secure Multi-Tier Cloud Infrastructure with Docker

A production-ready AWS network design built to maximize security and high availability. This project isolates the application layer inside a private subnet while safely exposing it via an Application Load Balancer (ALB).

## 🗺️ Architecture Overview
- **Custom VPC:** `10.0.0.0/16` CIDR block.
- **Public Subnets:** Hosts the Bastion Host (Jump Server) and Application Load Balancer.
- **Private Subnets:** Houses the application servers, completely hidden from the public internet.
- **NAT Gateway:** Configured to allow private servers to securely download Docker packages without exposing incoming ports.
- **Security Isolation:** Strict Security Groups allowing only Port 80 from the ALB to the app servers and Port 22 from the Bastion Host.

## 🚀 Tech Stack Used
- **Cloud Provider:** Amazon Web Services (AWS VPC, EC2, ALB, NAT Gateway, Internet Gateway, Route Tables)
- **Containerization:** Docker
- **Web Server:** Nginx
- **Terminal Management:** MobaXterm
- **OS:** Ubuntu 24.04 LTS

## 🔧 Deployment Steps
1. **Networking:** Provisioned custom VPC, subnets, Internet Gateway, and Route Tables.
2. **NAT Gateway:** Configured a NAT Gateway in the public subnet for private network internet access.
3. **Compute:** Deployed a Bastion Host in the public zone and an internal Web Server in the private zone.
4. **Security:** Restricted SSH access to the private server exclusively through the Bastion Host using safe `.pem` key pairs.
5. **Docker Deployment:** SSH'd into the private server via the Jump Server and deployed a containerized Nginx web server.
6. **Traffic Routing:** Created a Target Group and set up an Application Load Balancer (ALB) to route external web traffic to the private container.
