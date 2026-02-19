# 🚀 React App – DevOps CI/CD Deployment (Jenkins + Docker + AWS EC2)

## 📌 Project Overview

This project demonstrates a complete **DevOps CI/CD pipeline** for deploying a React application into a production‑ready environment using modern DevOps tools and practices.

The pipeline automates:

* Source code build
* Docker image creation
* Image push to Docker Hub
* Deployment on AWS EC2 server

---

## 🧰 Technologies & Tools Used

### ⚙️ DevOps Tools

* Git & GitHub (Version Control)
* Jenkins (CI/CD Automation)
* Docker (Containerization)
* Docker Hub (Image Repository)
* AWS EC2 (Deployment Server)
* Bash Scripting (Automation)

### ☁️ Architect Diagram
<img width="1536" height="1024" alt="ChatGPT Image Feb 19, 2026, 01_44_18 PM" src="https://github.com/user-attachments/assets/4acb6e00-0d2a-4123-882d-7b424cdb0ded" />

---


## 🔄 CI/CD Workflow

1. Developer pushes code to **dev branch** in GitHub
2. Jenkins pipeline triggers automatically
3. Jenkins builds Docker image
4. Image pushed to Docker Hub
5. Jenkins connects to EC2 server
6. Container deployed on port 80 (HTTP)

---

## 🐳 Docker Configuration

### Dockerfile

* Uses Node image
* Builds React app
* Serves app using Nginx

### docker-compose.yml

* Runs container in detached mode
* Maps port 80:80

---

## 🧪 Jenkins Pipeline Stages

### Stage 1 — Checkout Code

Pull latest code from GitHub dev branch

### Stage 2 — Build Docker Image

```
docker build -t react-app .
```

### Stage 3 — Push to Docker Hub

```
docker tag react-app kaviyapalaniveel/react-app:latest
docker push kaviyapalaniveel/react-app:latest
```

### Stage 4 — Deploy to EC2

```
docker pull kaviyapalaniveel/react-app:latest
docker run -d -p 80:80 kaviyapalaniveele/react-app:latest

<img width="884" height="411" alt="image" src="https://github.com/user-attachments/assets/1455eecb-8cce-4728-bba3-4eb16c509f2f" />

```

---

## 🖥️ Deployment Steps (Manual)

### Step 1 — Connect to EC2

```

### Step 2 — Install Docker

```
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```

### Step 3 — Run Container

```
docker run -d -p 80:80 react-app:latest
```

---

## 📜 Bash Scripts

### build.sh

Script to build Docker image

### deploy.sh

Script to deploy container to server
<img width="884" height="406" alt="image" src="https://github.com/user-attachments/assets/5b315dc1-49d8-4568-a2d9-b4cf47eaf8f8" />


---

## 🔐 Credentials & Security

* Docker Hub credentials stored in Jenkins
* SSH key used for EC2 access
* Sensitive data managed via Jenkins Credentials Manager

---

## ✅ Result

The React application is successfully deployed and accessible ,
```

---

## 📈 Advanced Improvements (Future Scope)

* Use Kubernetes for orchestration
* Implement Monitoring (Prometheus + Grafana)
* Add HTTPS using Nginx + SSL
* Auto scaling using AWS Load Balancer

---

