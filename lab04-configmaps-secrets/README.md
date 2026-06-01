# ConfigMaps & Secrets

Decouples configuration and credentials from container images. Config lives in the cluster, not in code — changing it doesn't require a rebuild or a redeploy of the image.

## ConfigMap

Stores non-sensitive key-value config. Injected into Pods as environment variables via `envFrom` (all keys) or `env.valueFrom.configMapKeyRef` (individual keys).

## Secret

Stores sensitive data base64-encoded. Access is controlled via RBAC — only authorised Pods and users can read them. Base64 is encoding, not encryption — Secrets are about access control, not confidentiality at rest.

In the AI platform: Ollama config comes from a ConfigMap. API keys and credentials come from Secrets — never hardcoded in manifests or committed to Git.

## Commands Reference

```bash
kubectl apply -f configmap.yaml
kubectl describe configmap <name> -n ai-platform
kubectl apply -f secret.yaml
kubectl get secret <name> -n ai-platform -o yaml

# Verify injection
kubectl exec -it <pod> -n ai-platform -- env | grep <KEY>