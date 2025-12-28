Project Name : Secure Cloud Homelab Web Platform (100% Free Tier)
Details : a secure Linux-based web app hosted on AWS EC2, backed by a database, isolated inside a VPC, with IAM, 
S3, and security hardening — while also using virtualization locally.

architecture diagram are in the architecture dir


Flow:
Laptop → SSH → EC2 (Linux) → App → Database
Static files → S3
Network isolation → VPC
Access control → IAM
Security → SSH keys, firewall, least privilege

🧱 PHASE 1 — Local Virtualization (Week 1)
Tools

VirtualBox (free)

Ubuntu Server ISO

Tasks

Create 2 VMs

VM1: Web Server

VM2: Database Server

Network mode: NAT + Host-only

SSH between VMs

Install:

sudo apt install nginx mysql-server ufw -y

Skills

✔ Virtualization
✔ Linux admin
✔ Internal networking

☁️ PHASE 2 — AWS Foundation (Week 2)
AWS Services (Free Tier)

EC2 t2.micro

VPC

IAM

S3

Tasks

Create custom VPC

Public subnet (web)

Internet Gateway

Route Table

Security Group:

Allow 22 (SSH)

Allow 80 (HTTP)

Launch EC2 (Ubuntu)

SSH into EC2

Install nginx

🔐 PHASE 3 — Security & IAM (Week 3)
IAM

Create IAM user

Attach least privilege policy

No root usage

EC2 Hardening
sudo adduser clouduser
sudo ufw allow ssh
sudo ufw allow http
sudo ufw enable


Disable root login

SSH keys only

Change SSH port (optional)

Skills

✔ Cloud security
✔ Identity & access

🗄️ PHASE 4 — Database Integration (Week 4)
Database

Install MySQL on EC2 OR

Use second EC2 (still free tier if careful)

sudo apt install mysql-server


Create DB + user

Bind to private IP

Security Group: DB port only from web server

📦 PHASE 5 — S3 Integration (Week 5)
Tasks

Create S3 bucket

Block public access

Upload static files

IAM Role for EC2:

S3 read-only access

aws s3 ls


Serve images/files from S3

Skills

✔ Object storage
✔ IAM roles

🌐 PHASE 6 — Networking Deep Dive (Week 6)
Add:

Private subnet

(Optional) Bastion host

Network ACLs

VPC Flow Logs (view only)

Learn:

Public vs Private IP

Routing

Security Group vs NACL

🧪 PHASE 7 — Security Testing (Week 7)

Fail2Ban

SSH brute-force protection

Logs:

/var/log/auth.log


Backup DB to S3

Principle of least privilege review

🧾 FINAL DELIVERABLE (Very Important)
GitHub Repo Structure
cloud-homelab-project/
├── architecture/
├── linux-notes/
├── networking/
├── security/
├── aws/
└── README.md

README MUST INCLUDE

Architecture diagram

Commands used

Security decisions

What broke & how you fixed it
