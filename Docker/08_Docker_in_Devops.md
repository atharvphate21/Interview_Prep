# 🐳 SECTION 8: Docker in DevOps

### How does Docker integrate with CI/CD?
> Docker integrates with CI/CD by building container images during the pipeline process.
>
> When code is pushed, the pipeline:
>
> 1. Pulls the source code
> 2. Builds a Docker image
> 3. Runs tests
> 4. Scans for vulnerabilities
> 5. Pushes the image to a registry
> 6. Deploys it to staging or production
>
> This ensures consistent deployments across environments.

### How do you tag Docker images?
> I tag Docker images using meaningful version identifiers like semantic versioning or commit SHA.

Example:

```bash
docker build -t myapp:1.2.0 .
docker tag myapp:1.2.0 myrepo/myapp:1.2.0
```

In CI:

```bash
docker build -t myrepo/myapp:$GIT_COMMIT .
```

### What is Docker image versioning strategy?
> We typically use:
>
> * Semantic versioning (v1.0.0)
> * Commit SHA for traceability
> * Environment-specific tags like latest, staging, prod
>
> Best practice is to avoid relying only on `latest` and instead use immutable version tags.

### How do you rollback a Docker deployment?
> To rollback, we redeploy the previous stable image tag.
>
> Since images are immutable, we simply redeploy the earlier version without rebuilding anything.
>
> This makes rollback fast and reliable.

### Why use commit SHA as image tag?
> Using commit SHA ensures every image version is uniquely traceable to a specific code commit.
>
> It improves debugging, auditing, and reproducibility in production environments.

### How do you push image in pipeline?
> In CI pipeline, after building the image:
>
> 1. Login to registry
> 2. Tag the image
> 3. Push the image

Example:

```bash
docker login
docker build -t myrepo/myapp:$GIT_COMMIT .
docker push myrepo/myapp:$GIT_COMMIT
```

### How do you manage multi-environment images?
> We use:
>
> * Same image across environments
> * Different configuration using environment variables
> * Separate deployment pipelines for dev, staging, and prod
>
> We avoid rebuilding images for each environment to maintain consistency.

### How to optimize Docker build in CI?
> To optimize build:
>
> * Use multi-stage builds
> * Use lightweight base images
> * Leverage Docker layer caching
> * Minimize build context using `.dockerignore`
> * Cache dependencies properly
>
> This reduces build time significantly.

### What is Docker build cache?
> Docker build cache reuses previously built layers if instructions haven’t changed.
>
> If a layer changes, all layers after it are rebuilt.
> That’s why ordering Dockerfile instructions properly is important.

### How to reduce pipeline build time?
> To reduce pipeline time:
>
> * Use layer caching
> * Avoid rebuilding unchanged layers
> * Use parallel jobs
> * Use smaller base images
> * Use prebuilt base images
> * Cache package dependencies
> * Use shallow Git clone
>
> These practices significantly improve CI performance.

👉 “What’s your real tagging strategy?”
> We use semantic versioning for releases, commit SHA for traceability, and avoid mutable tags like latest in production. Each deployment references an immutable image tag.