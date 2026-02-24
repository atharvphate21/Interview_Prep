# ☸️ SECTION 10: Troubleshooting (Highly Important)

### Pod is stuck in Pending. Why?
> A Pod stays in Pending usually due to:
>
> * Insufficient CPU or memory on nodes
> * Node selector or affinity mismatch
> * Taints without tolerations
> * PVC not bound
>
> I check:

```bash
kubectl describe pod <pod-name>
```

> It usually shows the scheduling reason.

### Pod is in CrashLoopBackOff. Why?
> CrashLoopBackOff happens when a container keeps crashing and restarting repeatedly.
> Common reasons:
>
> * Application error
> * Wrong environment variables
> * Database not reachable
> * Port already in use
>
> I check logs:

```bash
kubectl logs <pod-name>
```

### Pod is OOMKilled. Why?
> OOMKilled means the container exceeded its memory limit.
> Kubernetes killed it to protect the node.
>
> Solution:
>
> * Increase memory limit
> * Optimize application memory usage

### Service not reachable. Why?
> Common reasons:
>
> * Pod not running
> * Wrong port mapping
> * Service selector mismatch
> * Network policy blocking traffic
> * Ingress misconfiguration
>
> I verify:

```bash
kubectl get svc
kubectl get endpoints
kubectl describe svc <service>
```

### Node is NotReady. Why?
> A Node becomes NotReady if:
>
> * kubelet stopped
> * Network issue
> * Disk pressure
> * Memory pressure
>
> I check:

```bash
kubectl describe node <node-name>
```

### How do you debug a failing Pod?
> My approach:
>
> 1. Check Pod status
> 2. Describe Pod
> 3. Check logs
> 4. Check events
> 5. Verify resource limits
> 6. Check connectivity

Commands:

```bash
kubectl get pod
kubectl describe pod
kubectl logs
```

### How to check logs of a Pod?
```bash
kubectl logs <pod-name>
```

For multi-container Pod:

```bash
kubectl logs <pod-name> -c <container-name>
```

### How to exec into a Pod?
```bash
kubectl exec -it <pod-name> -- /bin/sh
```

Used for debugging inside container.

### How to describe a resource?
```bash
kubectl describe <resource-type> <name>
```

Example:

```bash
kubectl describe pod mypod
```

### Deployment not updating. Why?
> Possible reasons:
>
> * Image tag not changed
> * ImagePullPolicy set to IfNotPresent
> * Rollout paused
> * Readiness probe failing
>
> I check rollout status:

```bash
kubectl rollout status deployment <name>
```

### Pods restarting frequently. Why?
> Common causes:
>
> * CrashLoopBackOff
> * Liveness probe failing
> * Resource limits exceeded
> * Application bug

### Cluster is slow. How do you troubleshoot?
> I check:
>
> * Node CPU and memory usage
> * API server latency
> * etcd health
> * Pod resource usage
> * HPA behavior
>
> Commands:

```bash
kubectl top nodes
kubectl top pods
```

### How do you check cluster health?
> I check:
>
> * Node status
> * Component status
> * etcd health
>
> Commands:

```bash
kubectl get nodes
kubectl get componentstatuses
```

### How to debug DNS issues?
> Steps:
>
> * Check CoreDNS Pods
> * Exec into Pod and test DNS
>
> Example:

```bash
kubectl exec -it <pod> -- nslookup service-name
```

### How to debug networking issues?
> I check:
>
> * Service configuration
> * Endpoints
> * Network policies
> * Pod connectivity using curl or ping
> * CNI plugin health

Commands:

```bash
kubectl get svc
kubectl get endpoints
kubectl describe networkpolicy
```

👉 “What is your general troubleshooting approach?”
> I follow a layered approach:
> Check Pod → Service → Node → Networking → Logs → Resource usage → Events.