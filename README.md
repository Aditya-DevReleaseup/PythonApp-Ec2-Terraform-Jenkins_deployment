🚀 Jenkins CI/CD for Containerized AWS Deployments
(Docker • Terraform • EC2 )

This repository demonstrates production-style CI/CD pipelines using Jenkins to build, push, and deploy Python applications as containers on AWS.

The focus is on modern container workflows, using Terraform , push to docker-hub or ecr for securing images.

✔ Jenkins Declarative Pipelines
✔ Dockerized Python applications
✔ Infrastructure as Code using Terraform
✔ Secure AWS access using IAM Roles
✔ Amazon ECR or docker-hub for container images
✔ Parameter-based Apply / Destroy workflows

🏗️ Supported Deployment Models
1️⃣ Jenkins + Terraform + Docker (Build Stage)

Jenkins builds a Docker image for a Python application

Image is versioned and prepared for deployment

Same Docker image used across environments

Use case: Standardized container builds

2️⃣ Jenkins + Terraform + ECR + ECS (Fargate)

Jenkins builds Docker image

Pushes image to Amazon ECR or Docker-hub

Jenkins supports Apply / Destroy using parameters

Use case:
✔ Production-grade deployments
✔ Serverless containers (no EC2 management)

🧩 High-Level Architecture
GitHub
  ↓
Jenkins (CI/CD)
  ├── Docker Build
  ├── Push Image to ECR
  └── Terraform
        ├── APPLY  → makes infra Ec2 with docker install then build image , push image, pull image from ecr/docker-hub , runs python app.
        └── DESTROY → Tear Down all old infra to create new one for fresh builds.
  ↓
Amazon ECS (Fargate)

📁 Repository Structure
.
├── app/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── terraform/
│   ├── provider.tf
│   ├── main.tf
│   ├── variables.tf
│   ├── terraform.tfvars
│   └── outputs.tf
│
└── Jenkinsfile

🔐 Security Best Practices Used

✅ IAM Roles for Jenkins (no AWS access keys)

✅ No secrets in Jenkinsfile

✅ Terraform .tfvars for environment config

✅ Parameter-based approval (no input() issues)

▶️ Jenkins Pipeline Controls
Deploy Infrastructure & App
Build with Parameters → ACTION=apply

Destroy Infrastructure
Build with Parameters → ACTION=destroy


This approach avoids Jenkins UI deadlocks and is CI/CD friendly.

🧪 Jenkins Patterns Used

Declarative pipelines

Docker build & push

Terraform lifecycle management

Environment isolation using tfvars

Idempotent deployments

🧠 Interview-Ready Summary

“This project demonstrates a Jenkins-driven CI/CD pipeline that builds Docker images, pushes them to Amazon ECR, and deploys containerized applications on Amazon Ec2.”

🛠️ Prerequisites

Jenkins (running on EC2)

Docker

Terraform

AWS CLI

IAM Role attached to Jenkins EC2 with:

ECR

IAM

CloudWatch

VPC permissions

🚀 When to Use This Approach
Requirement	Solution
Containerized apps	Docker
Secure image storage	ECR
Repeatable infra	Terraform
Safe approvals	Jenkins parameters
🏁 Final Notes

This repository is designed to reflect:

Modern DevOps practices

Production-ready container deployments

Secure AWS authentication

Clean, maintainable Jenkins pipelines

----

🤝 Connect With Me - 📧 [Click here](https://www.linkedin.com/in/aditya-sharma-pr/)
