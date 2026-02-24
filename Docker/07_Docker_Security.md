# 🐳 SECTION 7: Docker Security

### How do you secure Docker containers?
> To secure Docker containers, I follow best practices such as:
>
> * Using minimal base images like Alpine or distroless
> * Running containers as non-root users
> * Scanning images for vulnerabilities
> * Using read-only file systems when possible
> * Limiting container resources
> * Enabling seccomp and AppArmor profiles
> * Avoiding hardcoded secrets in images

### What is rootless Docker?
> Rootless Docker allows running Docker daemon and containers without root privileges.
> It improves security by reducing the risk of privilege escalation attacks.

### What is Docker Content Trust?
> Docker Content Trust ensures that images are signed and verified before being pulled or run.
> It prevents running tampered or untrusted images.

### What is image scanning?
> Image scanning checks Docker images for vulnerabilities in OS packages and dependencies.
> Tools like Trivy, Clair, or Docker Scout are commonly used to detect security risks before deployment.

### How to avoid running container as root?
> To avoid running as root:
>
> * Use `USER` instruction in Dockerfile
> * Create a non-root user inside the container
> * Avoid using root in Kubernetes pod specs

Example:

```dockerfile
RUN adduser -D appuser
USER appuser
```

### What is USER instruction?
> The `USER` instruction in Dockerfile specifies which user will run the container processes.
> It improves security by preventing containers from running as root.

### What are namespaces in Docker?
> Namespaces provide isolation between containers.
> They isolate:
>
> * Process IDs
> * Network
> * Mount points
> * Users
>
> This ensures containers do not interfere with each other.

### What are cgroups?
> Control groups (cgroups) limit and manage resource usage like CPU, memory, and disk I/O for containers.
> They ensure fair resource allocation and prevent one container from consuming all resources.

### What is seccomp?
> Seccomp is a Linux security feature that restricts system calls a container can make.
> Docker uses a default seccomp profile to reduce attack surface.

### How to prevent container privilege escalation?
> To prevent privilege escalation:
>
> * Run containers as non-root
> * Use `--cap-drop` to remove unnecessary Linux capabilities
> * Avoid using `--privileged` mode
> * Enable seccomp and AppArmor
> * Use read-only root filesystem
> * Follow least privilege principle

👉 “How do you secure containers in CI/CD?”
> We integrate image scanning tools in the pipeline, enforce non-root containers, sign images, and only deploy trusted tagged versions to production.