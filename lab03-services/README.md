# Services & Networking

Services provide a stable network endpoint for a dynamic set of Pods. As Pods are created and destroyed, the Service IP and DNS name remain constant — consumers never need to track individual Pod IPs.

## Service Types

**ClusterIP** — internal only. Default type. Used for Pod-to-Pod communication inside the cluster. Ollama uses this so only Open WebUI can reach it.

**LoadBalancer** — provisions a cloud load balancer with a public IP. Used for Open WebUI so users can access it from a browser. One LoadBalancer per Service — use Ingress (Lab 07) to share one load balancer across multiple Services.

## Key Insight

K8s has built-in DNS. Every Service gets a hostname matching its name. A Pod can reach `http://nginx-clusterip` without knowing any IP — the cluster DNS resolves it. This is how Open WebUI will reach Ollama via `http://ollama:11434` in the final platform.

## Commands Reference

```bash
kubectl get service -n ai-platform
kubectl apply -f clusterip.yaml
kubectl delete service <name> -n ai-platform

# Test internal DNS from inside the cluster
kubectl run test-pod --image=busybox -it --rm -n ai-platform -- wget -O- http://<service-name>
