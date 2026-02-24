# ☸️ SECTION 7: Kubernetes Security (Production Critical)

### What is RBAC?
> RBAC stands for Role-Based Access Control.
> It controls who can access Kubernetes resources and what actions they can perform, based on roles and permissions.

### What is Role vs ClusterRole?
> Role defines permissions within a specific namespace.
> ClusterRole defines permissions across the entire cluster or for cluster-level resources.

### What is RoleBinding vs ClusterRoleBinding?
> RoleBinding grants permissions defined in a Role or ClusterRole within a namespace.
> ClusterRoleBinding grants cluster-wide permissions.

### What is ServiceAccount?
> A ServiceAccount provides identity to Pods.
> Applications inside Pods use it to authenticate with the Kubernetes API server.

### What is Pod Security Admission?
> Pod Security Admission is a built-in admission controller that enforces security policies on Pods.
> It replaces the older PodSecurityPolicy and ensures Pods follow defined security standards.

### What is Pod Security Standard?
> Pod Security Standard defines security levels for Pods:
>
> * Privileged
> * Baseline
> * Restricted
>
> Restricted is the most secure and recommended for production.

### What is admission controller?
> Admission controllers intercept API requests before objects are persisted in etcd.
> They validate or modify requests to enforce security policies or other rules.

### What is seccomp?
> Seccomp restricts system calls that a container can make.
> It reduces the attack surface by limiting access to sensitive Linux kernel operations.

### What is AppArmor?
> AppArmor is a Linux security module that restricts container capabilities based on predefined security profiles.

### What is network segmentation?
> Network segmentation limits communication between Pods using Network Policies.
> It ensures that only allowed traffic flows between services.

### What is TLS in Kubernetes?
> TLS encrypts communication between cluster components like API server and kubelet.
> It ensures secure communication using certificates.

### How do you secure etcd?
> To secure etcd:
>
> * Enable TLS encryption
> * Restrict access using authentication
> * Enable encryption at rest
> * Take regular backups
>
> etcd should never be publicly exposed.

### What is encryption at rest?
> Encryption at rest ensures that sensitive data like Secrets stored in etcd are encrypted on disk.
> It protects data even if storage is compromised.

### How do you manage secrets securely?
> Best practices include:
>
> * Using Kubernetes Secrets
> * Enabling encryption at rest
> * Using external secret managers like AWS Secrets Manager or HashiCorp Vault
> * Avoid storing secrets in Git
> * Restricting RBAC access

### How do you rotate secrets?
> Secret rotation involves:
>
> * Updating the secret value
> * Restarting Pods to pick up the new secret
> * Automating rotation using external secret managers
>
> In production, rotation should be automated and periodic.

### What is image pull secret?
> Image pull secret is used to authenticate with private container registries.
> It stores registry credentials securely and allows Pods to pull private images.

👉 “What are top 3 security practices in Kubernetes?”
> Enable RBAC, enforce Pod Security Standards, and use Network Policies with encrypted secrets.