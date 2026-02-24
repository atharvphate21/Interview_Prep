# 🐳 SECTION 9: Docker Advanced

### What happens internally when you run `docker run`?
> When I run `docker run`, Docker performs multiple steps internally:
>
> 1. Checks if the image exists locally; if not, it pulls from registry
> 2. Creates a writable container layer on top of image layers
> 3. Sets up networking and mounts volumes
> 4. Applies cgroups and namespaces for isolation
> 5. Starts the container using a runtime like `runc`
>
> So essentially, `docker run` = pull (if needed) + create + start.

### What is Union Filesystem?
> Union filesystem allows multiple layers to be stacked on top of each other to appear as a single filesystem.
>
> Docker images are built using layered architecture, and union filesystem merges these layers efficiently.
>
> It enables image reuse and storage optimization.

### What is container runtime?
> A container runtime is software responsible for running containers.
> It manages low-level tasks like creating namespaces, applying cgroups, and starting container processes.
>
> Examples include `runc` and `containerd`.

### What is runc?
> `runc` is a low-level container runtime that actually creates and runs containers according to OCI standards.
>
> Docker uses `runc` underneath to start containers.

### What is containerd?
> `containerd` is a higher-level container runtime responsible for managing container lifecycle, image transfer, and storage.
>
> Docker uses containerd internally to manage containers.

### Difference between Docker and containerd?
> Docker is a complete container platform with CLI, API, build tools, and registry support.
>
> containerd is a container runtime focused only on running and managing containers.
>
> Docker sits on top of containerd.

### What is OCI?
> OCI stands for Open Container Initiative.
> It defines industry standards for container runtime and image formats.
>
> Docker and other runtimes follow OCI standards to ensure compatibility.

### What is distroless image?
> A distroless image contains only the application and its runtime dependencies.
> It does not include package managers, shells, or unnecessary tools.
>
> This reduces attack surface and improves security.

### What is scratch vs alpine?
> `scratch` is an empty base image with nothing in it.
> It is used for statically compiled applications like Go.
>
> `Alpine` is a minimal Linux distribution with a small footprint, but still includes a package manager and shell.
>
> Scratch is smaller; Alpine is more flexible.

### What is image manifest?
> An image manifest is a JSON file that describes a Docker image.
>
> It includes:
>
> * Image layers
> * Architecture
> * OS
> * Metadata
>
> It helps Docker pull the correct image version, especially in multi-architecture images.

👉 “What happens when a container writes data?”
> Docker creates a writable layer on top of image layers. Any changes made by the container are stored in that writable layer without modifying the original image.