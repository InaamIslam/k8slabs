# Persistent Volumes

Container filesystems are ephemeral — data written inside a container is lost when the Pod dies. Persistent Volumes decouple storage from the Pod lifecycle, so data survives restarts, crashes, and rescheduling.

## Key Concepts

**PersistentVolumeClaim (PVC)** — a request for storage. On DigitalOcean, creating a PVC automatically provisions a real block storage volume via the `do-block-storage` StorageClass.

**volumeMounts** — mounts the PVC into the container at a specified path. The Pod writes to that path like a normal directory, unaware it's backed by a network volume.

## Key Insight

Ollama downloads AI models (4-8GB each) on first run and caches them to disk. Without a PVC, every Pod restart triggers a full re-download. With a PVC, the models persist indefinitely — the volume outlives any individual Pod.

## Commands Reference

```bash
kubectl apply -f pvc.yaml
kubectl get pvc -n ai-platform
kubectl describe pvc <name> -n ai-platform

# Verify data persistence
kubectl exec -it <pod> -n ai-platform -- ls /data
