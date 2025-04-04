---
title: Getting your software ready
---

### Decision Matrix

| Problem domain | Description | Reason for importance | Tool recommendation |
|:---:|:---:|:---:|:---:|
| Image Registry | A common place to store and fetch images | High availability, secure access control | [Harbor](ADRs/harbor_as_image_registry.md) |
| Secret Management | Securely store and manage sensitive information like passwords and API keys | Prevent unauthorized access and data leaks | [Sealed Secrets](ADRs/sealed_secrets_as_secret_management.md) |
| Ingress Controller / Gateway API | Manage external access to services in the cluster | Enable routing, load balancing, and secure communication | |
| GitOps / Deployment Pipelines | Automate application deployments using Git as the source of truth | Ensure consistency, traceability, and faster deployments | |
| Monitoring Infrastructure | Observe and analyze the health and performance of the cluster and applications | Proactive issue detection and resolution | |
| Service Mesh | Manage service-to-service communication within the cluster | Enable observability, security, and traffic control | |
| Network Policies | Define rules for communication between pods and services | Enhance security by restricting unauthorized traffic | |
| Authorization Integration | Manage user and service access to cluster resources | Enforce role-based access control and compliance | |
| Container Scanning | Identify vulnerabilities in container images | Ensure secure and compliant deployments | |
