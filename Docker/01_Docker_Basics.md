# 🐳 SECTION 1: Docker Basics

### What is Docker?
> Docker is a containerization platform that allows us to package an application along with its dependencies into a container. This ensures the application runs consistently across different environments like development, testing, and production.

### What problem does Docker solve?
> Docker solves the “it works on my machine” problem.
> It ensures consistency across environments by packaging the application, runtime, libraries, and dependencies together.
> It also improves portability, scalability, and deployment speed.

### Difference between Docker and Virtual Machine?
> The main difference is that virtual machines virtualize hardware, while Docker containers virtualize the operating system.
>
> VMs have their own OS and are heavier, whereas containers share the host OS kernel and are lightweight and faster to start.

### What is containerization?
> Containerization is the process of packaging an application and its dependencies into a lightweight, portable unit called a container, which can run consistently across different environments.

### What is Docker architecture?
> Docker architecture follows a client-server model.
> It consists of:
>
> * Docker Client
> * Docker Daemon
> * Docker Engine
> * Docker Registry
>
> The client sends commands to the daemon, which builds and runs containers.

### What are Docker images?
> A Docker image is a read-only template used to create containers.
> It contains application code, runtime, libraries, and dependencies required to run the application.

### What are Docker containers?
> A Docker container is a running instance of a Docker image.
> It is lightweight, isolated, and contains everything needed to run the application.

### What is Docker Engine?
> Docker Engine is the core component that enables building, running, and managing containers.
> It includes the Docker daemon, REST API, and CLI.

### What is Docker daemon?
> The Docker daemon is a background service that manages Docker objects like images, containers, networks, and volumes.
> It listens to Docker API requests and executes them.

### What is Docker client?
> The Docker client is the command-line interface that users interact with.
> It sends commands like `docker build` and `docker run` to the Docker daemon.

### What is Docker Hub?
> Docker Hub is a public cloud-based registry where Docker images are stored and shared.
> It allows us to pull official images or push our own images.

### What is a Docker registry?
> A Docker registry is a storage system for Docker images.
> It can be public like Docker Hub or private like AWS ECR or Harbor.

### What is the difference between image and container?
> An image is a static template.
> A container is a running instance of that image.
>
> You can create multiple containers from a single image.

### What is a base image?
> A base image is the starting point of a Docker image.
> It usually contains a minimal OS like Ubuntu, Alpine, or Debian, on top of which we build our application.

### What is scratch image?
> Scratch is an empty base image with no OS or dependencies.
> It is used to build extremely minimal images, usually for statically compiled applications like Go binaries.
