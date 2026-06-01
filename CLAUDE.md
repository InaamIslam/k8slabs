# k8slabs — CKA Study + AI Platform Project

## Who I am
Learning Kubernetes for the CKA exam. Building a real AI inference platform on K8s as a portfolio project for GitHub and job applications.

## Cluster
- Provider: DigitalOcean
- Node: `k8slabspool-33uf8p` (1 node, K8s v1.35.1)
- Context already configured in kubeconfig

## Project Goal
Build a self-hosted AI inference platform on K8s:
- **Ollama** — LLM runtime (model serving)
- **Open WebUI** — chat frontend
- Production patterns throughout: namespaces, RBAC, PVCs, Ingress, HPA, NetworkPolicies, monitoring

## Lab Structure
Each lab = one folder + README + YAML manifests + a git commit.

| Lab | Topic | Status |
|-----|-------|--------|
| lab01-pods-namespaces | Pods, Namespaces | ✅ Done |
| lab02-deployments | Deployments, ReplicaSets | ✅ Done |
| lab03-services | ClusterIP, NodePort, LoadBalancer | ✅ Done |
| lab04-configmaps-secrets | ConfigMaps, Secrets | ✅ Done |
| lab05-persistent-volumes | PV, PVC, StorageClass | 🔄 In progressg |
| lab06-resource-limits-hpa | LimitRange, HPA | ⏳ Pending |
| lab07-ingress | Ingress controller, TLS | ⏳ Pending |
| lab08-rbac | Roles, RoleBindings, ServiceAccounts | ⏳ Pending |
| lab09-troubleshooting | Break + fix scenarios | ⏳ Pending |
| ai-platform | Final project — Ollama + Open WebUI | ⏳ Pending |

## How I like to work with Claude
- I want to type commands myself — guide me, don't do it for me
- Explain the WHY before each step
- Remind me when to make a git commit
- One step at a time — wait for me to confirm before moving on

## Current Position
**Lab 01 — Step 1:** Setting up repo structure (git init, mkdir lab01-pods-namespaces)
