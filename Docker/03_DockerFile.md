# 🐳 SECTION 3: Dockerfile

### What is a Dockerfile?
> A Dockerfile is a text file that contains a set of instructions used to build a Docker image.
> It defines the base image, application code, dependencies, environment variables, and commands required to run the application.

### Explain Dockerfile lifecycle.
> The Dockerfile lifecycle follows this flow:
>
> 1. Start with a base image using `FROM`
> 2. Install dependencies using `RUN`
> 3. Copy application files using `COPY`
> 4. Set working directory using `WORKDIR`
> 5. Configure environment variables
> 6. Define default command using `CMD` or `ENTRYPOINT`
>
> Then we build the image using `docker build` and run it using `docker run`.

### Difference between CMD and ENTRYPOINT?
> `CMD` provides default arguments and can be overridden easily at runtime.
> `ENTRYPOINT` defines the main executable and cannot be easily overridden.
>
> In simple terms:
> ENTRYPOINT is the fixed main command, and CMD provides default parameters.

### Difference between COPY and ADD?
> `COPY` simply copies files from host to container.
> `ADD` can also extract compressed files and download files from URLs.
>
> Best practice is to use COPY unless you specifically need ADD features.

### What is WORKDIR?
> WORKDIR sets the working directory inside the container.
> All subsequent instructions like RUN, CMD, and COPY will execute relative to this directory.

Example:

```dockerfile
WORKDIR /app
```

### What is ENV in Dockerfile?
> ENV sets environment variables inside the container.
> These variables are available at runtime.

Example:

```dockerfile
ENV NODE_ENV=production
```

### What is EXPOSE?
> EXPOSE informs Docker that the container listens on a specific port.
> It does not publish the port — it is mainly documentation.
> Port publishing is done using `-p` in `docker run`.

### What is multi-stage build?
> Multi-stage build allows using multiple FROM statements in a Dockerfile.
>
> It is commonly used to build an application in one stage and copy only the final build artifacts into a smaller runtime image.
>
> This significantly reduces image size.

### What is layer caching?
> Each Dockerfile instruction creates a new image layer.
> Docker caches these layers.
> If a layer does not change, Docker reuses the cached layer, speeding up builds.

### Why should we minimize image layers?
> More layers increase image size and build complexity.
> Fewer optimized layers improve performance, reduce storage, and speed up deployment.

### How to reduce Docker image size?
> To reduce image size:
>
> * Use lightweight base images like Alpine
> * Use multi-stage builds
> * Remove unnecessary dependencies
> * Combine RUN commands
> * Use `.dockerignore`
> * Avoid installing build tools in production images

### What is `.dockerignore`?
> `.dockerignore` specifies files and folders that should not be sent to Docker during build.
> It reduces build context size and improves performance.

Example:

```
node_modules
.git
.env
```

### What is ONBUILD?
> ONBUILD is a special instruction that triggers when the image is used as a base image for another build.
> It is mainly used to create reusable base images.

### What is ARG?
> ARG defines build-time variables that are only available during image build.
> Unlike ENV, ARG values are not available in the running container.

Example:

```dockerfile
ARG VERSION=1.0
```

### Difference between RUN, CMD, ENTRYPOINT?
> `RUN` executes commands during image build time.
> `CMD` defines default command at container runtime.
> `ENTRYPOINT` defines the main executable that runs when container starts.
>
> So RUN is build-time, CMD and ENTRYPOINT are runtime.

👉 “Why multi-stage build is important in production?”
> It reduces image size, removes build dependencies from production images, improves security, and speeds up deployment.
