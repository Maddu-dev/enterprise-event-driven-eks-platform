# Enterprise Event-Driven EKS Platform
## Overview
This repository showcases a **production-grade, enterprise-ready, event-drivenmicroservices platform** built on **AWS EKS** using **Terraform-first infrastructure**,**Kafka (MSK) for asynchronous processing**, **event-driven autoscaling with KEDA**,and **GitOps-based continuous delivery**.
The platform is intentionally designed to mirror **real-world enterprise systems**with strong focus on:- Scalability- Security & encryption- Automation- Observability & SRE practices- Cost efficiency- Platform engineering best practices
---
## Business Use Case
An **Order & Inventory Management Platform** where:
- Users access the system via a public domain- Orders are submitted through REST APIs- Orders are published as Kafka events- Inventory & payment services consume events asynchronously- Redis provides high-speed caching- EFS provides shared persistent storage- Services scale dynamically based on **Kafka consumer lag**
This architecture decouples services and enables **resilient, scalable processing**under variable traffic.
---
## High-Level Architecture
```textUsers  ↓Route53 (Public DNS)  ↓ALB Ingress Controller + TLS (ACM) + WAF  ↓Amazon EKS (Kubernetes)  ├── Frontend Service (HPA)  ├── Order Service (Kafka Producer)  ├── Inventory Service (Kafka Consumer – KEDA)  ├── Payment Service (Async Worker – KEDA)  ↓Amazon MSK (Kafka)  ↓ElastiCache Redis (OSS)  ↓Amazon EFS (Shared Storage)
 Encryption at rest using AWS KMS Autoscaling via HPA + KEDA + Cluster Autoscaler GitOps-based deployments using ArgoCD
