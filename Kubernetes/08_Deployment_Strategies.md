# ☸️ SECTION 8: Deployment Strategies

### What is rolling update?
> Rolling update is the default deployment strategy in Kubernetes.
> It gradually replaces old Pods with new ones, ensuring the application remains available during the update.

### What is recreate strategy?
> Recreate strategy terminates all existing Pods before creating new ones.
> This causes downtime and is usually used for applications that cannot run multiple versions simultaneously.

### What is blue-green deployment?
> In blue-green deployment, we run two identical environments:
> Blue (current production) and Green (new version).
> After testing Green, we switch traffic from Blue to Green.

### What is canary deployment?
> Canary deployment releases a new version to a small percentage of users first.
> If it works fine, we gradually increase traffic to the new version.

### What is maxSurge and maxUnavailable?
> These are rolling update parameters.
>
> maxSurge defines how many extra Pods can be created during update.
> maxUnavailable defines how many Pods can be unavailable during update.

Example:
If replicas = 4 and maxUnavailable = 1, at least 3 Pods must stay running.

### How do you rollback deployment?
> We rollback using:

```bash
kubectl rollout undo deployment myapp
```

> Kubernetes maintains revision history, so we can revert to a previous stable version.

### What is kubectl rollout?
> kubectl rollout is used to manage and monitor Deployment updates.
> It can:
>
> * Check rollout status
> * Pause or resume deployment
> * Rollback to previous version

Example:

```bash
kubectl rollout status deployment myapp
```

### How do you achieve zero downtime?
> Zero downtime is achieved using rolling updates with proper readiness probes.
>
> The new Pod must pass readiness checks before traffic is routed to it, ensuring users don’t experience disruption.

### What are readiness and liveness probes?
> Liveness probe checks if the application is running properly.
> If it fails, the container is restarted.
>
> Readiness probe checks if the application is ready to serve traffic.
> If it fails, traffic is stopped but container is not restarted.

### What is startup probe?
> Startup probe checks whether the application has started successfully.
> It is useful for slow-starting applications and prevents liveness probe from killing the container too early.

👉 “How do readiness probes help in rolling updates?”
> Readiness probes ensure that new Pods receive traffic only after they are fully ready, preventing downtime during updates.