# 🐳 SECTION 10: Scenario-Based Docker

### Container is crashing immediately. How do you debug?
> First I check the container logs to see the exact error. If it exits too fast, I run it in interactive mode or override the entrypoint to get a shell. Then I validate the command, env variables, ports, and file paths inside the container.

**Commands I typically use:**

```bash
docker ps -a
docker logs <container>
docker inspect <container>
docker run --rm -it --entrypoint sh <image>
```

### Application works locally but not inside container. Why?
> Usually it’s due to environment differences. Common causes are missing dependencies, wrong environment variables, wrong file paths, incorrect port binding, or the app binding to `localhost` instead of `0.0.0.0`. I check logs, verify env vars, and confirm exposed/listening ports inside the container.

* Env variables not set
* App listening on `127.0.0.1` not `0.0.0.0`
* Missing OS packages/runtime
* Wrong working directory / volume path
* File permission issues

### Docker build is very slow. How to optimize?
> I optimize by improving Dockerfile caching and reducing build context. I reorder instructions so dependencies install first, I use `.dockerignore`, multi-stage builds, and small base images. In CI, I enable layer caching and avoid rebuilding unchanged layers.

What I’d say:
* Put rarely-changing layers first (dependencies)
* Use `.dockerignore`
* Multi-stage builds
* Cache dependencies (npm/pip/maven)
* Use lightweight base images

### Container cannot connect to another container. Why?
> Most commonly it’s a networking issue: containers are on different networks, incorrect hostname, wrong port, or the target service isn’t listening on the right interface. In Compose, services should connect using service names on the same network.

How I debug:

```bash
docker network ls
docker network inspect <network>
docker exec -it <container> ping <service-name>
docker exec -it <container> nc -zv <service-name> <port>
```

Common causes:

* Not in same network
* Using `localhost` instead of service name
* Port mismatch
* Firewall rules / published port misunderstanding

### Data is lost after container restart. Why?
> Because containers are ephemeral. If the application stores data inside the container filesystem, it will be lost when the container is recreated or removed. To persist data, I use volumes or bind mounts.

* Use Docker volumes for DB/data
* Bind mounts for dev
* Verify volume is actually mounted

### Image size is 2GB. How do you reduce it?
> I reduce image size by using multi-stage builds, smaller base images, removing build tools from runtime images, combining RUN commands, cleaning package caches, and using `.dockerignore` to avoid copying unnecessary files.

Strong points:
* Multi-stage build (build stage + runtime stage)
* Alpine/distroless where possible
* Remove caches (`apt-get clean`, remove `node_modules` from build context)
* Don’t copy `.git`, logs, artifacts

### Container is consuming too much memory. What will you do?
> First I confirm memory usage using Docker stats. Then I check application memory leaks, logs, and container limits. In production, I set memory limits and monitor usage, and if required I tune JVM/Node/Python memory settings.

* Check usage: `docker stats`
* Add limits: `--memory`, `--cpus`
* Fix memory leak in app
* Tune runtime (JVM heap, Node options)
* Add monitoring/alerts

### How do you implement zero-downtime deployment with Docker?
> For zero-downtime, I use rolling updates behind a load balancer. In practice, this is usually done using Kubernetes or Docker Swarm. Another approach is blue-green deployment where I run the new version in parallel, switch traffic, and then stop the old one.

Key approaches:

* Rolling update
* Blue-green deployment
* Health checks before switching traffic
* Load balancer / reverse proxy (Nginx/Traefik)

### How do you scan Docker images for vulnerabilities?
> We scan images in CI/CD before pushing or deploying. Tools like Trivy, Docker Scout, or Clair check OS packages and dependencies for known CVEs. We fail the pipeline if critical vulnerabilities are found.
* Scan during build pipeline
* Enforce policy gates (block critical CVEs)
* Rebuild regularly to patch base image vulnerabilities

###  How do you handle secrets in Docker?
> I never bake secrets into the image. I pass secrets at runtime using environment variables, secret managers, or orchestrator secrets like Docker Swarm secrets or Kubernetes secrets. For production, we use a secret manager like AWS Secrets Manager or HashiCorp Vault.

Best practices:

* No secrets in Dockerfile / Git
* Use secret managers
* Use runtime injection
* Restrict access (least privilege)
* Rotate secrets