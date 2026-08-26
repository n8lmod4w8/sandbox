# kubectl debug cheatsheet

Useful commands for day-to-day troubleshooting.

## Pods

```bash
# Get events sorted by time
kubectl get events --sort-by='.lastTimestamp'

# Show pod labels
kubectl get pods --show-labels

# Restart a deployment (rolling restart)
kubectl rollout restart deployment/<name>

# CrashLoopBackOff: inspect previous container
kubectl logs <pod> --previous
```

## Nodes

```bash
# Check node conditions and pressure
kubectl describe nodes | grep -A 10 'Conditions:'

# Get resource usage
kubectl top nodes
kubectl top pods -A
```

## Networking

```bash
# Temporary client pod for connectivity tests
kubectl run nettest --image=nicolaka/netshoot --rm -it -- /bin/bash

# Port forward for local debugging
kubectl port-forward svc/<service> 8080:80
```

## Contexts

```bash
# Switch namespace permanently (context)
kubectl config set-context --current --namespace=<ns>

# List all contexts
kubectl config get-contexts
```
