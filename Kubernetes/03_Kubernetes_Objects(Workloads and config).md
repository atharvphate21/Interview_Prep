# ☸️ SECTION 3: Kubernetes Objects (Workloads & Config)

# 🔹 Workloads

### What is a Pod?
> A Pod is the smallest deployable unit in Kubernetes.
> It represents one or more containers running together on the same node, sharing the same network and storage.

### Why is Pod the smallest unit?
> Because Kubernetes does not deploy containers directly.
> It always deploys containers inside a Pod, which provides shared networking and storage.
> So Pod is the atomic scheduling unit.

### Can a Pod have multiple containers?
> Yes. A Pod can have multiple containers that share the same network namespace and volumes.
> This is commonly used for sidecar patterns like logging or proxy containers.

### What is a Deployment?
> A Deployment is a higher-level object used to manage Pods and ReplicaSets.
> It provides features like rolling updates, rollback, and scaling.

### What is ReplicaSet?
> ReplicaSet ensures that a specified number of Pod replicas are running at all times.
> If a Pod crashes, ReplicaSet automatically creates a new one.

### Difference between Pod and Deployment?
> A Pod is a single instance of a container or group of containers.
> A Deployment manages multiple Pods and provides update and scaling capabilities.

### What is StatefulSet?
> StatefulSet is used to manage stateful applications.
> It provides stable network identities, persistent storage, and ordered deployment.

### When do you use StatefulSet over Deployment?
> I use StatefulSet when applications require:
>
> * Stable Pod names
> * Persistent storage
> * Ordered startup and shutdown
>
> Example: databases like MySQL, MongoDB.

### What is DaemonSet?
> A DaemonSet ensures that a Pod runs on every node in the cluster.
> It is commonly used for logging agents, monitoring agents, or security tools.

### What is Job?
> A Job creates one or more Pods to complete a specific task and ensures they successfully finish.
> It is used for batch processing.

### What is CronJob?
> A CronJob runs Jobs on a scheduled basis using cron syntax.
> It is used for periodic tasks like backups.

# 🔹 Configuration

### What is Namespace?
> Namespace is a logical isolation mechanism within a Kubernetes cluster.
> It allows multiple teams or environments to share the same cluster without conflicts.

### What is ConfigMap?
> ConfigMap is used to store non-sensitive configuration data like environment variables or config files.
> It decouples configuration from application code.

### What is Secret?
> Secret is used to store sensitive data like passwords, API keys, and tokens.
> It is base64 encoded and can be mounted as environment variables or files.

### Difference between ConfigMap and Secret?
> ConfigMap stores non-sensitive data.
> Secret stores sensitive data and is base64 encoded.
> Secrets are handled more securely in the cluster.

### What is Downward API?
> Downward API allows a Pod to access its own metadata, like Pod name, namespace, or labels, from inside the container.

### What is Init Container?
> An Init Container runs before the main application container starts.
> It is used for setup tasks like database migration or dependency checks.

### What is Sidecar container?
> A Sidecar container runs alongside the main container inside the same Pod.
> It is commonly used for logging, monitoring, or proxy services.

### What is Ephemeral container?
> An Ephemeral container is a temporary container added to a running Pod for debugging purposes.
> It is not restarted and is mainly used with `kubectl debug`.

👉 “What is the relationship between Deployment, ReplicaSet, and Pod?”
> Deployment manages ReplicaSet, and ReplicaSet manages Pods.