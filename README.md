# Kubernetes AI Platform

Production-grade AI inference platform built on Kubernetes. The project deploys a self-hosted LLM serving stack (Ollama + Open WebUI) on DigitalOcean Kubernetes, applying real-world platform engineering patterns throughout.

## Architecture

```
ai-platform namespace
├── Ollama          — LLM runtime, model serving via REST API
├── Open WebUI      — Chat interface, multi-model support
├── Ingress         — TLS termination, external access
└── Prometheus      — Metrics, autoscaling signals
```

## Labs

Each lab isolates a core Kubernetes concept and feeds directly into the platform build.

| Lab | Topic |
|-----|-------|
| [lab01](lab01-pods-namespaces/) | Pods & Namespaces |
| [lab02](lab02-deployments/) | Deployments & ReplicaSets |
| [lab03](lab03-services/) | Services & Networking |
| [lab04](lab04-configmaps-secrets/) | ConfigMaps & Secrets |
| [lab05](lab05-persistent-volumes/) | Persistent Volumes |
| [lab06](lab06-resource-limits-hpa/) | Resource Limits & Autoscaling |
| [lab07](lab07-ingress/) | Ingress & TLS |
| [lab08](lab08-rbac/) | RBAC |
| [lab09](lab09-troubleshooting/) | Troubleshooting |

## Stack

- **Cluster:** DigitalOcean Kubernetes (v1.35.1)
- **LLM Runtime:** Ollama
- **Frontend:** Open WebUI
- **Ingress:** NGINX Ingress Controller
- **Monitoring:** Prometheus + Grafana
