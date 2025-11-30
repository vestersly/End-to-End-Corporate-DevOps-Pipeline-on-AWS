# End-to-End Corporate DevOps Pipeline on AWS

## Overview
This project demonstrates a production-style DevOps CI/CD pipeline built on AWS that automates the complete software delivery lifecycle for a Java-based application — from source code commit to containerized deployment on Kubernetes.

It reflects an enterprise-inspired architecture and is designed as a practical learning project to showcase cloud engineering, automation, and security integration.

---

## Architecture Highlights

### Cloud & Infrastructure
- Multi-AZ Amazon VPC design with public and private subnets  
- Secure NAT Gateway for private outbound traffic  
- Bastion Host for administrative access  
- Amazon EKS for container orchestration  
- Amazon ECR for container image storage  

### CI/CD Pipeline
- Jenkins Pipeline as Code (Jenkinsfile)
- Maven for builds and testing
- Sonatype Nexus for artifact management
- GitHub as source control

### Security & DevSecOps
- SonarQube for static code analysis
- Trivy for container vulnerability scanning
- Kube-audit for Kubernetes posture checks
- IAM and access isolation applied throughout

### Observability
- AWS CloudWatch logging and monitoring
- Pipeline status alerts via Amazon SNS
- (Optional) Prometheus & Grafana integration

---

## Technology Stack

| Area | Tools |
|------|-------|
| Cloud | AWS (EC2, VPC, EKS, ECR, IAM, SNS) |
| CI/CD | Jenkins, GitHub, Maven |
| DevSecOps | SonarQube, Trivy, Kube-audit |
| Containers | Docker, Kubernetes |
| Artifacts | Nexus Repository |
| Monitoring | CloudWatch |
| Application | Java / Spring Boot |

---

## How This Project Is Used

1. AWS infrastructure is provisioned (VPC, subnets, nodes).
2. Jenkins builds and tests code automatically.
3. SonarQube scans the codebase.
4. Artifacts are stored in Nexus.
5. Docker images are scanned and pushed to ECR.
6. Kubernetes deploys the application on EKS.
7. Logs and notifications are handled via CloudWatch and SNS.

---

## Purpose of this Project
This project was built as a hands-on learning initiative to:
- Practice AWS architecture patterns  
- Build CI/CD automation workflows  
- Integrate security into deployment pipelines  
- Simulate enterprise-style environments  

---

## Author
Sylvester Awungjia  
AWS Certified Solutions Architect | Cybersecurity
