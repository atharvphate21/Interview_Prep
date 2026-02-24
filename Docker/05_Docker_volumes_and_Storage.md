# 🐳 SECTION 5: Docker Volumes & Storage

### What is Docker volume?
> A Docker volume is a persistent storage mechanism used to store data outside the container’s writable layer.
> It allows data to persist even if the container is stopped or removed.

### Difference between volume and bind mount?
> A **volume** is managed by Docker and stored in Docker’s default directory.
> A **bind mount** directly maps a host directory to the container.
>
> Volumes are preferred in production because they are more portable and managed by Docker.
> Bind mounts are often used in development for local file changes.

### Where are volumes stored?
> By default, Docker stores volumes in:
>
> `/var/lib/docker/volumes/`
>
> However, this location depends on the Docker installation and storage driver.

### What is tmpfs mount?
> tmpfs mount stores data in the host’s memory instead of disk.
>
> It is temporary and data is lost when the container stops.
>
> It is useful for sensitive data or temporary caching.

### How to persist container data?
> To persist data, I use Docker volumes or bind mounts when running the container.

Example with volume:

```bash
docker run -v myvolume:/app/data myapp
```

This ensures data is stored outside the container lifecycle.

### What happens to data when container is removed?
> If data is stored inside the container’s writable layer, it is deleted when the container is removed.
>
> If data is stored in a volume, it remains even after the container is deleted.

### How to inspect a volume?
> I use:

```bash
docker volume inspect volume_name
```

This shows details like mount path and driver information.

### How to backup Docker volume?
> One way is to use a temporary container to tar the volume data.

Example:

```bash
docker run --rm -v myvolume:/data -v $(pwd):/backup busybox tar czf /backup/backup.tar.gz /data
```

This creates a compressed backup file on the host.

👉 “Why should we avoid storing data inside container?”
> Containers are ephemeral by design. If the container crashes or is recreated, data stored inside it is lost. That’s why we use volumes for persistence.