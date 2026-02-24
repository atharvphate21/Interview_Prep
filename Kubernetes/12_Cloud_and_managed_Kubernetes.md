# ☸️ SECTION 12: Cloud & Managed Kubernetes

### What is Amazon EKS?
> Amazon EKS (Elastic Kubernetes Service) is a managed Kubernetes service provided by AWS.
> AWS manages the control plane components, and users manage the worker nodes and workloads.

### What is Google Kubernetes Engine?
> Google Kubernetes Engine (GKE) is Google Cloud’s managed Kubernetes service.
> It provides automated cluster management, upgrades, and scaling.

### What is Azure Kubernetes Service?
> Azure Kubernetes Service (AKS) is Microsoft Azure’s managed Kubernetes platform.
> It simplifies deployment, scaling, and management of Kubernetes clusters.

### Difference between self-managed and managed Kubernetes?
> In self-managed Kubernetes, we install and manage everything including control plane, etcd, upgrades, and security.
>
> In managed Kubernetes like EKS, GKE, or AKS, the cloud provider manages the control plane, reducing operational overhead.

### What is IAM integration with Kubernetes?
> IAM integration allows Kubernetes to use cloud provider identity and access management.
>
> It controls which users or services can access cluster resources securely.

### What is IRSA in EKS?
> IRSA stands for IAM Roles for Service Accounts.
>
> It allows Kubernetes Pods to assume specific IAM roles securely without storing AWS credentials inside the container.

### How does LoadBalancer work in cloud?
> When we create a Service of type LoadBalancer, Kubernetes requests the cloud provider to provision a cloud load balancer.
>
> The cloud load balancer forwards external traffic to the NodePort service, which routes traffic to Pods.

### How do you upgrade Kubernetes cluster?
> In managed Kubernetes:
>
> * Upgrade control plane first
> * Upgrade node groups
> * Verify compatibility
>
> We ensure workloads are compatible and perform upgrades gradually to avoid downtime.

### How do you backup etcd?
> etcd backup is done using etcd snapshot commands.
>
> In managed services, cloud providers handle etcd backup automatically.
>
> In self-managed clusters, we take periodic etcd snapshots and store them securely.

### How do you handle multi-region deployment?
> Multi-region deployment is implemented by:
>
> * Running clusters in multiple regions
> * Using global load balancers
> * Replicating data across regions
> * Implementing disaster recovery strategies

### How do you implement high availability?
> High availability is achieved by:
>
> * Multiple control plane nodes
> * Multiple worker nodes
> * Running multiple Pod replicas
> * Using load balancers
> * Enabling auto-scaling

### How do you reduce Kubernetes costs?
> Cost optimization strategies include:
>
> * Right-sizing resource requests and limits
> * Using Cluster Autoscaler
> * Using spot instances
> * Removing unused resources
> * Monitoring idle workloads
> * Using HPA to scale based on demand

👉 “What’s the difference between EKS and self-managed cluster in terms of operations?”
> In EKS, AWS manages control plane availability, security patches, and etcd management, while in self-managed clusters, we are responsible for all operational tasks.