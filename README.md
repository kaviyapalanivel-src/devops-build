🚀 Project Title

Production-Ready React Application Deployment using DevOps CI/CD Pipeline with Monitoring

📌 Project Overview

This project demonstrates an end-to-end DevOps workflow to deploy a production-ready React application using containerization, CI/CD automation, cloud deployment, and monitoring. The application is Dockerized and deployed on an AWS EC2 instance, with Jenkins automating build, push, and deployment processes based on branch triggers. Separate Docker Hub repositories are maintained for development and production images. Infrastructure security is configured using AWS Security Groups. Monitoring is implemented using Prometheus, Node Exporter, and Grafana to track application health and server metrics, with alerts configured for downtime scenarios.

🧱 Architecture Flow
Developer → GitHub (dev branch) → Jenkins CI
→ Docker Build → Push to DockerHub (dev)

Merge dev → main → Jenkins CI/CD
→ Docker Build → Push to DockerHub (prod)
→ Deploy to AWS EC2 → Monitoring

⚙️ Steps Performed
1️⃣ Application Setup

Cloned React application repository

Built application for production

Configured to run on Port 80 (HTTP)

git clone https://github.com/kaviyapalanivel-src/devops-build
cd devops-build

2️⃣ Dockerization
Created Dockerfile

Multi-stage build for optimized image

Nginx used to serve production build

Docker Compose

Container orchestration for deployment

3️⃣ Bash Automation Scripts
build.sh

Builds Docker image

deploy.sh

Runs container on EC2

4️⃣ Version Control (Git CLI)

Code pushed to dev branch

Used .gitignore and .dockerignore

Feature → dev → main workflow followed

5️⃣ Docker Hub Repositories

Created two repositories:

Repo	Visibility	Purpose
dev	Public	Development builds
prod	Private	Production builds
6️⃣ Jenkins CI/CD Pipeline

Configured Jenkins to:

✔ Connect to GitHub repository
✔ Auto-trigger builds

Branch Logic
🔹 If code pushed to dev branch:

Build Docker image

Push to Docker Hub dev repo

🔹 If dev merged to main:

Build production image

Push to Docker Hub prod repo

Deploy to EC2 server

7️⃣ AWS Deployment
EC2 Setup

Instance type: t2.micro

OS: Linux

Security Group Rules
Port	Access
80	Public (Application access)
22	My IP only (SSH access)
📊 Monitoring Setup

Monitoring implemented using open-source tools:

🔹 Prometheus

Collects application and server metrics

🔹 Node Exporter

Provides system metrics (CPU, Memory, Disk)

🔹 Grafana

Visualizes metrics using dashboards

🛠 Monitoring Installation via Scripts

Monitoring components installed using custom scripts:

prometheus.sh

node_exporter.sh

grafana.sh

Execution Steps
chmod +x prometheus.sh node_exporter.sh grafana.sh

./prometheus.sh
./node_exporter.sh
./grafana.sh

❤️ Health Monitoring

Prometheus configured to monitor:

Application uptime

Server metrics

Grafana dashboards display:

CPU usage

Memory usage

System load

Application status

Alerts configured to notify if application goes down.

🌐 Deployment Output

Application accessible via EC2 Public IP on port 80

Monitoring dashboards accessible via Grafana
