# Enterprise Event-Driven EKS Platform
## Overview
This repository showcases a **production-grade, enterprise-ready, event-driven microservices platform**built on **AWS EKS** using **Terraform-first infrastructure**, **Kafka (AWS MSK) for asynchronousprocessing**, **event-driven autoscaling with KEDA**, and **GitOps-based continuous delivery**.
The platform is intentionally designed to mirror **real-world enterprise systems** with a strongfocus on:
- Scalability
- Security & encryption
- Automation
- Observability & SRE practices
- Cost efficiency
- Platform engineering best practices  
---
## Business Use Case
An **Order & Inventory Management Platform** where:
- Users access the system via a public domain- Orders are submitted through REST APIs
- Orders are published as Kafka events
- Inventory & payment services consume events asynchronously
- Redis provides high-speed caching
- EFS provides shared persistent storage
- Services scale dynamically based on **Kafka consumer lag**, not just CPU

  This architecture enables **loose coupling**, **high throughput**, and **resilient processing** during traffic spikes.
---
## High-Level Architecture
```text
Users
  ↓
Route53 (Public DNS)
   ↓
ALB Ingress Controller + TLS (ACM) + WAF  ↓Amazon EKS (Kubernetes)
   ├── Frontend Service (HPA)
   ├── Order Service (Kafka Producer)
   ├── Inventory Service (Kafka Consumer – KEDA)
   ├── Payment Service (Async Worker – KEDA)
   ↓
Amazon MSK (Kafka)
   ↓
ElastiCache Redis (OSS)
   ↓
Amazon EFS (Shared Storage)

Encryption at rest using AWS KMS Autoscaling via HPA + KEDA + Cluster Autoscaler GitOps-based deployments using ArgoCD
---
## Technology Stack

##☁️ Cloud & AWS Services

- Amazon EKS
- Amazon MSK (Kafka)
- ElastiCache Redis (OSS)
- Amazon EFS
- AWS KMS
- ALB / NLB
- Route53
- AWS WAF
- CloudWatch

##🏗️ Infrastructure as Code

- Terraform (modular, remote state, multi-environment)
- Helm (platform add-ons)

##☸️ Containers & Orchestration
- Docker
- Kubernetes (EKS)
- Helm

##🔁 CI/CD & GitOps

- GitHub Actions (CI)
- Docker Hub (container registry)
- ArgoCD (GitOps CD)

##📊 Observability & SRE
- Prometheus
- Grafana
- ELK / EFK
- Loki
- Tempo
- SLIs / SLOs

##🔐 Security & DevSecOps
- KMS encryption
- IAM & IRSA
- OPA / Gatekeeper
- Trivy
- Secrets scanning

##🧑‍💻 Automation & Scripting
- Bash
- Python

