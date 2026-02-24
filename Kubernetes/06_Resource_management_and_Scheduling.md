# ☸️ SECTION 6: Resource Management & Scheduling

### What is resource request and limit?
> Resource request is the minimum amount of CPU or memory a container needs.
> Resource limit is the maximum amount it is allowed to use.
>
> The scheduler uses request to place the Pod on a node, and limit enforces the usage cap.

### What happens if CPU limit is exceeded?
> If CPU usage exceeds the limit, Kubernetes throttles the container.
> It does not kill the Pod, but restricts CPU usage to the defined limit.

### What happens if memory limit is exceeded?
> If memory usage exceeds the defined limit, the container is terminated by the system and marked as OOMKilled.

### What is OOMKilled?
> OOMKilled means “Out Of Memory Killed.”
> The container was terminated because it exceeded its memory limit.

### What is CPU throttling?
> CPU throttling happens when a container tries to use more CPU than its defined limit.
> The system restricts its CPU usage instead of killing it.

### What is QoS class (Guaranteed, Burstable, BestEffort)?
> Kubernetes assigns QoS classes based on resource configuration:
>
> Guaranteed – Requests and limits are equal for CPU and memory.
> Burstable – Requests and limits are defined but not equal.
> BestEffort – No requests or limits defined.
>
> Guaranteed Pods are least likely to be evicted.

### What is LimitRange?
> LimitRange sets default resource requests and limits for Pods in a namespace.
> It prevents users from creating Pods without resource constraints.

### What is ResourceQuota?
> ResourceQuota limits total resource usage in a namespace, such as total CPU, memory, or number of Pods.
> It ensures fair resource allocation among teams.

### How does Pod eviction happen?
> Pod eviction happens when a node is under resource pressure like memory or disk pressure.
> Kubernetes evicts lower-priority Pods to protect cluster stability.

### What are eviction thresholds?
> Eviction thresholds define resource pressure limits like memory.available or node disk pressure.
> When thresholds are crossed, Kubernetes starts evicting Pods.

### What is HPA?
> HPA stands for Horizontal Pod Autoscaler.
> It automatically scales the number of Pod replicas based on CPU or custom metrics.

### How does HPA work internally?
> HPA monitors metrics from Metrics Server or Prometheus.
> It compares current usage against target utilization and adjusts replica count accordingly.

Example:
If CPU target is 50% and current is 80%, it increases replicas.

### What is VPA?
> VPA stands for Vertical Pod Autoscaler.
> It adjusts CPU and memory requests/limits of Pods instead of scaling replica count.

### What is Cluster Autoscaler?
> Cluster Autoscaler automatically adds or removes worker nodes based on resource demand.
> It works with cloud providers like AWS or GCP.

### How to scale manually?
> We can scale manually using:

```bash
kubectl scale deployment myapp --replicas=5
```

### What is taint and toleration?
> Taints are applied to nodes to repel certain Pods.
> Tolerations allow Pods to be scheduled on tainted nodes.
>
> It is used to reserve nodes for specific workloads.

### What is node affinity?
> Node affinity defines rules to schedule Pods on specific nodes based on labels.
> It is more flexible than nodeSelector.

### What is pod affinity and anti-affinity?
> Pod affinity ensures Pods are scheduled close to specific other Pods.
> Pod anti-affinity ensures Pods are scheduled away from certain Pods.
>
> It is used for high availability and workload distribution.

### What is topology spread constraint?
> Topology spread constraints ensure Pods are evenly distributed across failure domains like zones or nodes.
> It improves availability and fault tolerance.

👉 “What happens if no requests are defined?”
> The Pod becomes BestEffort QoS and is most likely to be evicted during resource pressure.