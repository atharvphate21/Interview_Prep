# ☸️ SECTION 1: Kubernetes Fundamentals
## 🔹 Basics

### What is Kubernetes?
> Kubernetes is an open-source container orchestration platform used to automate deployment, scaling, and management of containerized applications. It helps manage containers efficiently in production environments.

### Why do we need Kubernetes?
> We need Kubernetes to manage containers at scale. When we have multiple containers running across multiple servers, Kubernetes helps with scheduling, scaling, self-healing, load balancing, and rolling updates automatically.

### What problem does Kubernetes solve?
> Kubernetes solves the problem of managing containerized applications in distributed environments. It handles scaling, failover, networking, and resource management so that applications remain highly available and resilient.

### What is container orchestration?
> Container orchestration is the automated management of container deployment, scaling, networking, and lifecycle. Kubernetes is the most widely used container orchestration platform.

### What is a Kubernetes cluster?
> A Kubernetes cluster is a group of machines (nodes) that run containerized applications. It consists of a control plane and worker nodes.

### What are the main components of Kubernetes?
> The main components are:
>
> * Control Plane components (API server, scheduler, controllers, etcd)
> * Worker node components (kubelet, kube-proxy, container runtime)

### What is the Control Plane?
> The Control Plane manages the entire cluster. It makes decisions about scheduling, scaling, and maintaining the desired state of the cluster.

### What is a Node?
> A Node is a machine in the Kubernetes cluster that runs application workloads. It can be a physical or virtual machine.

### What is Master Node?
> The Master Node, now called the Control Plane node, runs the control plane components like API server, scheduler, and controllers. It manages the cluster.

### What is Worker Node?
> A Worker Node runs the actual application containers. It contains kubelet, kube-proxy, and container runtime.

# 🔹 Core Components

### What is kube-apiserver?
> The kube-apiserver is the central component of the control plane. All communication with the cluster happens through it. It exposes the Kubernetes API and interacts with etcd.

### What is etcd?
> etcd is a distributed key-value store used to store all cluster data, including configuration and state information. It is the source of truth for the cluster.

### What is kube-scheduler?
> The kube-scheduler decides which worker node a Pod should run on, based on resource availability and constraints.

### What is kube-controller-manager?
> The kube-controller-manager runs controllers that ensure the cluster matches the desired state. For example, if a Pod crashes, it ensures a new one is created.

### What is cloud-controller-manager?
> The cloud-controller-manager integrates Kubernetes with cloud providers like AWS, Azure, or GCP. It manages resources like load balancers and storage in cloud environments.

### What is kubelet?
> kubelet runs on each worker node. It ensures containers are running as defined in the Pod specification and reports node status back to the control plane.

### What is kube-proxy?
> kube-proxy manages networking rules on each node. It enables communication between services and Pods using iptables or IPVS.

### What is container runtime in Kubernetes?
> The container runtime is the software responsible for running containers. Examples include containerd and CRI-O. Kubernetes interacts with it through CRI.

### What is the difference between Docker and Kubernetes?
> Docker is a container platform used to build and run containers. Kubernetes is an orchestration platform used to manage containers at scale.
> Docker creates containers, Kubernetes manages them.

### What is CRI (Container Runtime Interface)?
> CRI is an interface that allows Kubernetes to communicate with different container runtimes like containerd or CRI-O. It ensures Kubernetes is runtime-agnostic.

👉 “What happens when you create a Pod?”
API server → etcd → scheduler → kubelet → container runtime.
