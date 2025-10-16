# 🚪 AWS Fargate

- Serverless compute engine for containers.
- Runs containers without managing servers or clusters.
- Supports ECS and EKS.
- Pay-per-use.
- No infrastructure management done by the user.

## 🛜 Networking

- Tasks run inside your VPC → full network control.
- Supports integration with Application Load Balancer (ALB) or Network Load Balancer (NLB).

## 🔒 Security

- Shared responsibility model → AWS manages infrastructure security, you manage container/task security.
- No SSH access to underlying hosts.
- Cluster-level isolation between tasks.

## 🥸 Use Cases

- Long-running or scheduled background services.
- Workloads with unpredictable scaling needs.
- Running legacy or monolithic apps in containers.
- Batch processing and microservice deployments.
