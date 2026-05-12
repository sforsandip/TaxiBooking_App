# 🚕 Taxi Booking App — Full DevOps CI/CD Pipeline

A production-grade DevOps project demonstrating end-to-end automation of a Java-based Taxi Booking web application — from source code to Kubernetes deployment on AWS EKS.

---

## 🏗️ Architecture Overview

```
Developer Push (GitHub)
        ↓
  Jenkins CI/CD Pipeline
        ↓
  ┌─────────────────────────────────────────────────┐
  │  Maven Build → Unit Tests → SonarQube Analysis  │
  └─────────────────────────────────────────────────┘
        ↓
  WAR artifact → AWS S3 (artifact storage)
        ↓
  Docker Build → Push to AWS ECR
        ↓
  Ansible → Configure EC2 instances
        ↓
  Terraform → Provision AWS Infrastructure
        ↓
  Kubernetes (EKS) → Deploy & Scale Application
```

---

## 🛠️ Tech Stack

| Category | Tool |
|---|---|
| Application | Java (Maven), Tomcat 10 |
| CI/CD | Jenkins (Declarative Pipeline) |
| Code Quality | SonarQube (SonarCloud) |
| Containerization | Docker |
| Container Registry | AWS ECR |
| Artifact Storage | AWS S3 |
| Infrastructure as Code | Terraform |
| Configuration Management | Ansible |
| Orchestration | Kubernetes (AWS EKS) |
| Cloud Provider | AWS (EC2, EKS, ECR, S3) |

---

## 🚀 CI/CD Pipeline Stages

The Jenkins pipeline (`Jenkinsfile`) automates the following stages:

1. **Build** — Compiles the Java application using Maven (`mvn package`)
2. **Test** — Runs unit tests and generates Surefire reports
3. **SonarQube Analysis** — Static code analysis via SonarCloud for code quality & security
4. **Upload to S3** — Pushes the WAR artifact to an AWS S3 bucket for storage
5. **Docker Build** — Builds a Docker image using Tomcat 10 as base
6. **ECR Login** — Authenticates to AWS Elastic Container Registry
7. **Tag & Push** — Tags the image with build number and pushes to ECR
8. **Deploy** — Executes `deploy.sh` to roll out the latest image

---

## ☸️ Kubernetes Deployment

The `k8s/` and `EKS/` directories contain Kubernetes manifests for deploying the application on AWS EKS:

- Deployment configuration with rolling update strategy
- Service definitions for load balancing
- EKS cluster configuration for managed Kubernetes

---

## 🔧 Infrastructure (Terraform)

The `terraform_files/` directory provisions the AWS infrastructure including:

- VPC, subnets, and security groups
- EC2 instances for Jenkins and application servers
- EKS cluster setup
- ECR repository
- S3 bucket for artifact storage

---

## ⚙️ Configuration Management (Ansible)

The `Ansible/` directory contains playbooks for:

- Server provisioning and dependency installation
- Docker setup on EC2 instances
- Application configuration and deployment automation

---

## 📁 Project Structure

```
TaxiBooking_App/
├── Ansible/              # Ansible playbooks for server config
├── EKS/                  # AWS EKS cluster manifests
├── k8s/                  # Kubernetes deployment manifests
├── server/               # Backend server configuration
├── taxi-booking/         # Java Spring application source
├── terraform_files/      # Terraform IaC for AWS infrastructure
├── Dockerfile            # Docker image definition (Tomcat 10)
├── Jenkinsfile           # Declarative CI/CD pipeline
├── deploy.sh             # Deployment automation script
└── pom.xml               # Maven build configuration
```

---

## ⚡ Quick Start

### Prerequisites
- Jenkins server with Maven agent configured
- AWS CLI configured with appropriate IAM permissions
- Docker installed on build agent
- `kubectl` configured for EKS cluster
- Terraform >= 1.0 installed
- Ansible installed

### Running the Pipeline

1. Clone the repository:
   ```bash
   git clone https://github.com/sforsandip/TaxiBooking_App.git
   ```

2. Provision infrastructure with Terraform:
   ```bash
   cd terraform_files
   terraform init
   terraform plan
   terraform apply
   ```

3. Configure servers with Ansible:
   ```bash
   cd Ansible
   ansible-playbook -i inventory playbook.yml
   ```

4. Trigger the Jenkins pipeline — it will automatically build, test, containerize, and deploy the application.

---

## 🔒 Security Notes

- SonarCloud integration provides continuous security scanning
- Docker images are versioned with Jenkins build numbers (`v1.BUILD_NUMBER`)
- AWS IAM roles used for ECR and S3 access (no hardcoded credentials)
- Secrets managed via Jenkins credentials store

---

## 📊 Pipeline Flow

```
Code Push → Jenkins Trigger → Maven Build & Test
→ SonarQube Scan → S3 Upload → Docker Build
→ ECR Push → EKS Deployment
```

---

## 👨‍💻 Author

**Sandip** — Aspiring DevOps Engineer  
Transitioning from IT Admin & Network Support to Cloud & DevOps  
📍 Hyderabad, India

[![GitHub](https://img.shields.io/badge/GitHub-sforsandip-181717?logo=github)](https://github.com/sforsandip)

---

## 📌 Topics

`devops` `jenkins` `docker` `kubernetes` `terraform` `ansible` `aws` `eks` `ecr` `ci-cd` `sonarqube` `java` `maven`
