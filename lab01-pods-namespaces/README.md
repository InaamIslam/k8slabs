# Pods & Namespaces

Foundational workload isolation patterns on Kubernetes. This lab establishes the `ai-platform` namespace used throughout this project and explores the Pod lifecycle directly — the building block beneath every higher-level workload controller.

## Concepts

**Namespaces** provide logical isolation within a cluster. All resources for the AI inference platform are scoped to the `ai-platform` namespace, mirroring a real multi-tenant production setup where teams or environments are separated by namespace.

**Pods** are the atomic unit of execution in Kubernetes — one or more containers sharing a network stack and storage. In production, Pods are managed by controllers (Deployments, StatefulSets) rather than created directly. Understanding bare Pod behaviour is essential for debugging and for the failure modes those controllers are designed to handle.

## Key Takeaway

Bare Pods are mortal. Delete one and it's gone — no controller reschedules it. This is precisely the gap that Deployments (see `lab02`) fill, and understanding it is the foundation for reasoning about availability in any K8s-based system including ML inference workloads where uptime directly affects user experience.

## Commands Reference

```bash
# Create namespace
kubectl create namespace ai-platform

# Apply manifest
kubectl apply -f pod.yaml

# Inspect
kubectl get pods -n ai-platform
kubectl describe pod nginx-pod -n ai-platform
kubectl logs nginx-pod -n ai-platform

# Debug — exec into running container
kubectl exec -it nginx-pod -n ai-platform -- /bin/bash

# Teardown
kubectl delete pod nginx-pod -n ai-platform
```
