# 🐳 SECTION 4: Docker Networking

### ✅ What are Docker network drivers?

> Docker network drivers define how containers communicate with each other and the outside world.
> The main drivers are:
>
> * Bridge
> * Host
> * Overlay
> * None
> * Macvlan (advanced use case)

### ✅ What is bridge network?
> Bridge is the default network driver in Docker.
> It creates a private internal network on the host.
> Containers connected to the same bridge network can communicate with each other using IP addresses or container names.

### ✅ What is host network?
> In host networking, the container shares the host’s network stack.
> It does not get its own IP address.
> This removes network isolation but improves performance since there is no NAT.

### ✅ What is overlay network?
> Overlay network is used for communication between containers running on different Docker hosts.
> It is mainly used in Docker Swarm or distributed environments.
> It enables multi-host networking.

### ✅ What is none network?
> The none network disables networking completely.
> The container does not have external network access.
> It is used for highly isolated workloads.

### ✅ How do containers communicate?
> Containers communicate through Docker networks.
> If they are on the same bridge network, they can communicate using container names because Docker provides internal DNS resolution.
> Across hosts, overlay networks are used.

### ✅ What is port mapping?
> Port mapping maps a container’s internal port to a host machine port.
>
> Example:
>
> ```bash
> docker run -p 8080:80 nginx
> ```
>
> This maps port 80 inside the container to port 8080 on the host.

### ✅ What is Docker DNS?
> Docker provides built-in DNS for containers in user-defined networks.
> Containers can communicate using container names instead of IP addresses.
> This improves service discovery.

### ✅ How to create a custom network?
> I create a custom bridge network using:

```bash
docker network create mynetwork
```

Then run containers inside that network:

```bash
docker run --network mynetwork nginx
```

### ✅ Difference between bridge and overlay?
> Bridge network works on a single Docker host.
> Overlay network works across multiple Docker hosts.
>
> Bridge is used for local container communication, while overlay is used in clustered or distributed environments.

👉 “Why use custom bridge network instead of default bridge?”
> Custom bridge networks provide automatic DNS resolution between containers and better isolation compared to the default bridge network.