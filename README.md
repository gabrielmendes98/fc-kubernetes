# FC-Kubernetes

This repository serves as a practical learning environment for Kubernetes concepts using **Kind (Kubernetes in Docker)**, enabling local cluster management without cloud provider costs.

## Project Overview

- **Local Kubernetes Practice**: Uses Kind to create multi-node clusters (1 control-plane + 3 workers)
- **Cost Optimization**: Avoids cloud expenses while maintaining production-like environments
- **Full Stack Implementation**: Includes Go applications, MySQL stateful workloads, and monitoring components

## Repository Structure

- Docker file: Simple Go application containerization
- Docker compose: Local development environment setup
- Kubernetes resources (k8s folder): Cluster configuration and application deployment

## Key Features

1. **Cost Optimization**:

   - Local cluster management via Kind
   - Resource limits to prevent overconsumption

2. **Production Patterns**:

   - Horizontal Pod Autoscaling (HPA)
   - StatefulSet for MySQL with persistent storage
   - Network policies and ingress control

3. **Security**:

   - RBAC roles and service accounts
   - Secret management and config isolation
   - Pod security contexts

4. **Best Practices**:
   - Probes for resilience (startup/readiness/liveness)
   - Resource quotas and limits
   - Configuration separation (ConfigMaps/Secrets)

## Getting Started

1. Create cluster:

```bash
kind create cluster --config=k8s/kind.yaml --name=fullcycle
```

2. Deploy application:

```bash
kubectl apply -f k8s/
```

3. Test load balancing:

```bash
kubectl run -it fortio --rm --image=fortio/fortio -- load -qps 800 -t 120s -c 70 "http://goserver-service/healthz"
```
