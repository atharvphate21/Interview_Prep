# ☸️ SECTION 2: Kubernetes Architecture & Internals

### What happens internally when you create a Pod?
> When I create a Pod using `kubectl apply`, the request first goes to the kube-apiserver.
> The API server validates the request and stores the Pod definition in etcd.
>
> Then the scheduler detects the unscheduled Pod and assigns it to a suitable worker node.
>
> The kubelet on that node receives the Pod specification, pulls the container image, and instructs the container runtime to start the container.
>
> Finally, kube-proxy sets up networking so the Pod can communicate.

Simple flow:
**kubectl → API Server → etcd → Scheduler → kubelet → container runtime**

### What is reconciliation loop?
> The reconciliation loop is the core concept of Kubernetes controllers.
> It continuously compares the desired state stored in etcd with the current actual state of the cluster.
> If there is a difference, it takes corrective action to match the desired state.

Example:
If desired replicas = 3 and only 2 are running, it creates one more Pod.

### What are controllers in Kubernetes?
> Controllers are background processes that monitor cluster state and ensure it matches the desired configuration.
>
> Examples include:
>
> * ReplicaSet Controller
> * Deployment Controller
> * Node Controller
> * Job Controller

They run inside kube-controller-manager.

### What is leader election?
> Leader election is used in high availability setups.
> When multiple control plane instances are running, only one instance acts as the leader for certain components.
>
> If the leader fails, another instance takes over automatically.

### How does kube-scheduler make decisions?
> The scheduler first filters nodes based on constraints like resource availability, node selectors, taints, and affinity rules.
>
> Then it scores the remaining nodes based on factors like resource utilization and spreads workload evenly.
>
> Finally, it selects the best node for the Pod.

### What is watch mechanism?
> The watch mechanism allows components to continuously monitor changes in cluster resources.
>
> Instead of polling repeatedly, components subscribe to the API server and receive real-time updates when objects change.

### What is informer?
> Informer is a client-side caching mechanism built on top of the watch API.
>
> It reduces load on the API server by maintaining a local cache and notifying controllers about resource changes efficiently.

### How does API server communicate with etcd?
> The API server communicates with etcd using secure HTTPS-based REST APIs.
>
> All cluster state data is stored in etcd in key-value format, and only the API server interacts directly with etcd.

### How is data stored in etcd?
> etcd stores data as key-value pairs.
>
> Kubernetes objects like Pods, Deployments, and Services are stored in JSON format under structured keys.
>
> etcd ensures strong consistency and uses the Raft consensus algorithm.

### How does high availability work in control plane?
> In HA setup, multiple control plane nodes run API server, scheduler, and controller manager.
>
> etcd also runs as a clustered distributed system.
>
> A load balancer sits in front of API servers.
>
> If one control plane node fails, others continue serving requests.

### What happens during cluster startup?
> During startup:
>
> 1. etcd starts first
> 2. API server connects to etcd
> 3. Controller manager and scheduler start
> 4. Worker nodes register
> 5. CoreDNS and kube-proxy start
>
> Once all components are running, the cluster becomes ready.

### How does node registration happen?
> When kubelet starts on a worker node, it connects to the API server using certificates.
>
> It registers itself as a Node resource in the cluster and continuously sends heartbeats to indicate it is healthy.

### What is a static Pod?
> A static Pod is managed directly by the kubelet, not by the API server.
>
> Its manifest file is placed in a specific directory like `/etc/kubernetes/manifests`.
>
> Static Pods are commonly used for control plane components.

👉 “Why is etcd critical?”
> etcd is the source of truth. If etcd is down and no backup exists, the cluster state is lost.