# 🐳 SECTION 2: Docker Commands

### How do you build a Docker image?
> I build an image using a Dockerfile with `docker build`, providing a tag and build context.

```bash
docker build -t myapp:1.0 .
```

### How do you run a container?
> I use `docker run` to create and start a container from an image.

```bash
docker run -d --name myapp -p 8080:80 myapp:1.0
```

### Difference between `docker run` and `docker start`?
> `docker run` creates a **new** container and starts it.
> `docker start` starts an **existing stopped** container.

Example:

```bash
docker run --name c1 nginx
docker stop c1
docker start c1
```

### How do you list running containers?
> I use:

```bash
docker ps
```

To list all containers including stopped:

```bash
docker ps -a
```

### How do you stop a container?
> I stop it gracefully using:

```bash
docker stop <container_name_or_id>
```

Force stop (if needed):

```bash
docker kill <container_name_or_id>
```

### How do you remove a container?
> I remove a stopped container using:

```bash
docker rm <container_name_or_id>
```

Remove forcefully (running container):

```bash
docker rm -f <container_name_or_id>
```

### How do you remove an image?
> I remove an image using:

```bash
docker rmi <image_id_or_name:tag>
```

Remove unused images (cleanup):

```bash
docker image prune
```

### How do you check container logs?
> I use `docker logs`:

```bash
docker logs <container_name_or_id>
```

Follow logs live:

```bash
docker logs -f <container_name_or_id>
```

### How do you access a running container?
> I usually use `docker exec` to open a shell inside the container.

```bash
docker exec -it <container_name_or_id> /bin/bash
```

(For alpine images)

```bash
docker exec -it <container_name_or_id> /bin/sh
```

### How do you inspect a container?
> I use `docker inspect` to view detailed info like IP, mounts, env vars, and config.

```bash
docker inspect <container_name_or_id>
```

### What is `docker exec`?
> `docker exec` runs a new command inside an already running container, like opening a shell or running debugging commands.

Example:

```bash
docker exec -it myapp ls
docker exec -it myapp /bin/bash
```

### What is `docker attach`?
> `docker attach` connects my terminal to the main process of a running container.
> It’s mainly used to view or interact with the container’s primary process.

```bash
docker attach <container_name_or_id>
```

(Usually, I prefer `docker exec` for debugging because attach can interrupt the main process if not handled carefully.)

### How to copy files between host and container?
> I use `docker cp`.

Host → Container:

```bash
docker cp localfile.txt mycontainer:/path/
```

Container → Host:

```bash
docker cp mycontainer:/path/file.txt .
```

### How to tag an image?
> I tag an image using `docker tag`, usually before pushing to a registry.

```bash
docker tag myapp:1.0 username/myapp:1.0
```

### How to push image to Docker Hub?
> First I login, then push the tagged image.

```bash
docker login
docker push username/myapp:1.0
```
