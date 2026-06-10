# Resource Limits & Horizontal Pod Autoscaling

Unconstrained containers can exhaust node resources and starve other workloads. Resource limits cap consumption per container. HPA automatically scales replica count based on real-time metrics, handling traffic spikes without manual intervention.

## Resource Requests vs Limits

**Requests** — guaranteed minimum. Used by the scheduler to decide which node to place the Pod on.  
**Limits** — hard ceiling. CPU is throttled at the limit; memory over the limit kills the container.

```yaml
resources:
  requests:
    cpu: "100m"
    memory: "128Mi"
  limits:
    cpu: "500m"
    memory: "256Mi"

Commands Reference

kubectl get hpa -n ai-platform
kubectl describe hpa <name> -n ai-platform

# Install metrics-server (required for HPA)
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

# Patch HPA threshold on the fly
kubectl patch hpa <name> -n ai-platform --patch '{"spec":{"metrics":[{"type":"Resource","resource":{"name":"cpu","target":{"type":"Utilization","averageUtilization":50}}}]}}'