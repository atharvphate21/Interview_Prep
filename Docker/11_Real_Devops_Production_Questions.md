# 🐳 SECTION 11: Real DevOps Production Questions

### How do you manage Docker in Kubernetes?
> In Kubernetes, Docker images are used as container images inside Pods. Kubernetes handles orchestration, scaling, networking, and self-healing.
>
> We build and push Docker images to a registry, then reference them in Kubernetes deployment YAML files.
> Kubernetes manages replicas, rolling updates, and restarts failed containers automatically.

### What is image pull policy?
> Image pull policy defines when Kubernetes pulls an image from the registry.
>
> The options are:
>
> * `Always` – Pull every time container starts
> * `IfNotPresent` – Pull only if image not available locally
> * `Never` – Never pull from registry
>
> In production, we usually use `IfNotPresent` with versioned tags.

### What is Docker registry authentication?
> Docker registry authentication ensures only authorized users can push or pull images.
>
> We use `docker login` locally, and in CI/CD we use credentials stored securely as secrets.
>
> In Kubernetes, we use image pull secrets to authenticate with private registries.

### How do you clean unused Docker resources?
> I remove unused containers, images, volumes, and networks using Docker cleanup commands.
>
> Regular cleanup prevents disk space issues on servers.

### What is `docker system prune`?
> `docker system prune` removes unused containers, networks, images, and build cache.
>
> It helps free up disk space.
>
> We use it carefully in production environments.

Example:

```bash
docker system prune -a
```

### What is multi-architecture image?
> A multi-architecture image supports multiple CPU architectures like amd64 and arm64.
>
> Docker uses a manifest list to automatically pull the correct image version based on the system architecture.

### What is Docker healthcheck?
> Docker healthcheck defines a command to check whether a container is healthy.
>
> If the health check fails, orchestration tools can restart or replace the container.

Example in Dockerfile:

```dockerfile
HEALTHCHECK CMD curl --fail http://localhost:8080 || exit 1
```

### How do you monitor Docker containers?
> I monitor containers using tools like:
>
> * `docker stats` for basic metrics
> * Prometheus + Grafana for production monitoring
> * Cloud monitoring tools like Datadog or CloudWatch
>
> We monitor CPU, memory, disk usage, and container health.

### How do you implement logging?
> Best practice is to write application logs to stdout/stderr.
> Docker captures these logs and they can be:
>
> * Viewed with `docker logs`
> * Sent to centralized logging tools like ELK stack or Fluentd
>
> In Kubernetes, logs are aggregated using logging agents.

### How do you handle high availability with Docker?
> For high availability:
>
> * Run multiple container replicas
> * Use a load balancer
> * Use orchestration tools like Kubernetes or Docker Swarm
> * Enable health checks
> * Use rolling updates
>
> Kubernetes automatically restarts failed containers and maintains desired replica count.

👉 “How do you ensure production stability?”
> We use versioned images, health checks, monitoring, centralized logging, rolling deployments, and rollback strategies to ensure stability and quick recovery.