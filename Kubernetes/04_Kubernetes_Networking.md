# ☸️ SECTION 4: Kubernetes Networking

### How does Pod-to-Pod communication work?
> In Kubernetes, every Pod gets its own unique IP address.
> Pods can communicate directly with each other using their IPs without NAT, even if they are on different nodes.
> This is enabled by the cluster networking model and CNI plugins.

### How does Kubernetes assign IP addresses?
> When a Pod is created, the CNI plugin assigns it an IP address from the cluster’s Pod network range.
> Each Pod gets a unique IP within the cluster.

### What is CNI?
> CNI stands for Container Network Interface.
> It is a standard interface that allows Kubernetes to interact with different networking plugins to configure Pod networking.

### Name some CNI plugins.
> Common CNI plugins include:
>
> * Calico
> * Flannel
> * Cilium
> * Weave
>
> Calico is popular for network policies, and Cilium is known for eBPF-based networking.

### What is a Service?
> A Service is a Kubernetes object that exposes a set of Pods as a stable network endpoint.
> It provides a fixed IP and DNS name, even if Pods restart.

### Types of Services?
> The main types are:
>
> * ClusterIP
> * NodePort
> * LoadBalancer
> * ExternalName

### What is ClusterIP?
> ClusterIP is the default Service type.
> It exposes the Service internally within the cluster.

### What is NodePort?
> NodePort exposes the Service on a static port on each Node’s IP.
> It allows external access using NodeIP:NodePort.

### What is LoadBalancer?
> LoadBalancer exposes the Service externally using a cloud provider’s load balancer.
> It is mainly used in cloud environments like AWS or Azure.

### How does LoadBalancer service work?
> When a LoadBalancer Service is created, Kubernetes requests the cloud provider to provision a load balancer.
> That load balancer routes external traffic to the NodePort, which forwards traffic to the appropriate Pods.

### What is headless service?
> A headless Service does not assign a ClusterIP.
> It allows direct access to individual Pod IPs and is commonly used with StatefulSets.

### What is ExternalName service?
> ExternalName maps a Service to an external DNS name.
> It does not create a proxy; it just returns a DNS alias.

### What is Service discovery?
> Service discovery allows Pods to find and communicate with other Services using DNS names instead of IP addresses.

### What is CoreDNS?
> CoreDNS is the DNS server used in Kubernetes.
> It resolves Service names to their corresponding ClusterIP addresses.

### What is kube-proxy?
> kube-proxy runs on each node and maintains network rules to route traffic to the correct Pods.
> It uses iptables or IPVS for load balancing.

### Difference between iptables and IPVS mode?
> iptables uses rule-based packet filtering.
> IPVS provides better performance and scalability for large clusters because it uses a more efficient load balancing mechanism.

### What is Ingress?
> Ingress is a Kubernetes object that manages external HTTP and HTTPS access to Services.
> It provides routing based on hostnames or paths.

### What is Ingress Controller?
> An Ingress Controller is a component that implements Ingress rules.
> Examples include NGINX Ingress Controller and Traefik.

### Difference between Service and Ingress?
> Service exposes applications internally or externally.
> Ingress manages HTTP/HTTPS routing and provides advanced features like SSL termination and path-based routing.

### What is Network Policy?
> Network Policy defines rules to control traffic between Pods.
> It enhances security by allowing only specific traffic based on labels.

### What is Service Mesh?
> A Service Mesh is a dedicated infrastructure layer that manages service-to-service communication.
> It provides traffic management, security, observability, and retries.

### What is Istio?
> Istio is a popular Service Mesh implementation.
> It provides features like traffic routing, mTLS encryption, monitoring, and fault injection.

👉 “How does traffic flow from internet to Pod?”
> Internet → LoadBalancer → NodePort → Service → Pod → Container.