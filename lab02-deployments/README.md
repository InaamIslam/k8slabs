# Deployments & ReplicaSets

A Deployment controller maintains a desired number of Pod replicas at all times. It manages ReplicaSets under the hood — each image change creates a new ReplicaSet, enabling zero-downtime rolling updates and instant rollbacks.

## Key Operations

Rolling update — K8s shifts Pods from old ReplicaSet to new one gradually, maintaining availability throughout:

```bash
kubectl set image deployment/nginx-deployment nginx=nginx:1.25.0 -n ai-platform
kubectl rollout status deployment/nginx-deployment -n ai-platform
Rollback — reverts to previous ReplicaSet instantly:


kubectl rollout undo deployment/nginx-deployment -n ai-platform
Scaling:


kubectl scale deployment/nginx-deployment --replicas=5 -n ai-platform
Key Insight
Bare Pods from Lab 01 have no controller watching over them. Deployments fix this — self-healing, zero-downtime updates, and instant rollbacks are all emergent from the ReplicaSet mechanism. This is the pattern Ollama will use in the final platform.

Commands Reference

kubectl get deployments -n ai-platform
kubectl get replicasets -n ai-platform
kubectl rollout status deployment/<name> -n ai-platform
kubectl rollout undo deployment/<name> -n ai-platform
kubectl set image deployment/<name> <container>=<image> -n ai-platform
kubectl scale deployment/<name> --replicas=<n> -n ai-platform

