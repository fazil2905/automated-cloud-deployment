# 🚀 Automated Cloud Deployment Pipeline

This project implements an end-to-end CI/CD pipeline that automates application build, containerization, and deployment to AWS ECS using Jenkins, Docker, and Terraform.

---

## 📌 Overview

The pipeline enables continuous delivery by automatically building and deploying the application whenever changes are pushed to the repository.

**Workflow:**
GitHub → Jenkins → Docker → Docker Hub → Terraform → AWS ECS

---

## ⚙️ Pipeline Workflow

1. Developer pushes code to GitHub (`main` branch)
2. GitHub webhook triggers Jenkins pipeline
3. Jenkins builds Docker image from source code
4. Image is pushed to Docker Hub
5. Terraform initializes infrastructure
6. Terraform deploys/updates application on AWS ECS

---

## 🛠️ Tech Stack

* CI/CD: Jenkins
* Containerization: Docker
* Registry: Docker Hub
* Infrastructure as Code: Terraform
* Cloud: AWS ECS
* Version Control: GitHub

---

## 🔄 Pipeline Stages

* Build Docker Image
* Docker Authentication
* Push Image to Docker Hub
* Terraform Init
* Terraform Apply (ECS Deployment)

---

## 🔐 Credentials (Jenkins)

* docker-creds → Docker Hub authentication
* aws-creds → AWS access key and secret key

---

## 🌐 Automation Setup

* GitHub webhook triggers pipeline on every push
* Jenkins exposed using ngrok for webhook access

---

## 📂 Project Structure

```
├── app/                # Application code
├── terraform/          # Infrastructure configuration
├── Dockerfile          # Docker build instructions
├── Jenkinsfile         # CI/CD pipeline
└── README.md
```
---

## 🚀 Key Features

* Fully automated CI/CD pipeline
* Infrastructure managed as code
* Containerized deployment
* Continuous deployment to AWS ECS
* Secure credential handling

---

## 📈 Result

* No manual deployment
* Faster and consistent releases
* Scalable cloud deployment

---

## 👨‍💻 Author

Fazil Ahmed
