# 🐳 SECTION 6: Docker Compose

### What is Docker Compose?
> Docker Compose is a tool used to define and manage multi-container Docker applications.
> Instead of running multiple `docker run` commands, we define all services in a YAML file and start them together using a single command.

### What is `docker-compose.yml`?
> `docker-compose.yml` is a YAML configuration file where we define services, networks, volumes, environment variables, and dependencies for a multi-container application.

It typically includes:

* Services (like app, database, redis)
* Networks
* Volumes
* Environment variables

### How do you scale services in Docker Compose?
> We can scale services using the `--scale` option.

Example:

```bash
docker compose up --scale web=3
```

This runs 3 instances of the `web` service.

### Difference between Compose and Docker Swarm?
> Docker Compose is mainly used for local development and single-host setups.
> Docker Swarm is used for clustering and managing containers across multiple hosts.
>
> Swarm provides orchestration features like load balancing and high availability, while Compose is simpler and development-focused.

### How do services communicate in Compose?
> Services in Docker Compose automatically communicate using service names.
> Docker creates a default network, and internal DNS allows containers to resolve each other by service name.

Example:
If service name is `db`, the app connects using:

```
db:5432
```

### What is `depends_on`?
> `depends_on` defines service startup order in Docker Compose.
> It ensures that dependent services start before the current service.
>
> However, it does not guarantee that the service is fully ready — only that it has started.

### How to pass environment variables in Compose?
> Environment variables can be passed in multiple ways:

1. Directly inside `docker-compose.yml`
2. Using an `.env` file
3. Using `environment:` block

Example:

```yaml
environment:
  - DB_HOST=db
  - DB_PORT=5432
```

Or using `.env` file for better security and management.

👉 “Why use Compose in development?”
> Docker Compose simplifies multi-container setup, ensures consistency across environments, and allows developers to spin up full application stacks with a single command.