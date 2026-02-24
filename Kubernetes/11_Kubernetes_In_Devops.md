# ☸️ SECTION 11: Kubernetes in DevOps (CI/CD & GitOps)

### How does Kubernetes integrate with CI/CD?
> In a CI/CD pipeline, after code is built and tested, a Docker image is created and pushed to a container registry.
>
> Then Kubernetes deploys that image using Deployment manifests or Helm charts.
>
> The pipeline either directly updates the cluster using `kubectl apply` or updates a Git repository in a GitOps workflow.

Flow:
Code → Build → Test → Docker Image → Push → Deploy to Kubernetes

### What is Helm?
> Helm is a package manager for Kubernetes.
> It simplifies application deployment by packaging Kubernetes resources into reusable templates called charts.

### What is a Helm chart?
> A Helm chart is a collection of YAML templates and configuration files that define a Kubernetes application.
>
> It includes:
>
> * Templates folder
> * values.yaml
> * Chart.yaml
>
> It allows parameterized and reusable deployments.

### What is GitOps?
> GitOps is a deployment strategy where Git is the single source of truth for infrastructure and application configurations.
>
> Changes are made via Git commits, and a GitOps tool automatically syncs the cluster to match the repository state.

### What is ArgoCD?
> ArgoCD is a GitOps continuous delivery tool for Kubernetes.
> It continuously monitors a Git repository and ensures the cluster matches the desired state defined in Git.

### How does GitOps workflow work?
> The workflow is:
>
> 1. Developer updates Kubernetes manifests or Helm chart in Git
> 2. Changes are reviewed and merged
> 3. ArgoCD detects the change
> 4. ArgoCD syncs the cluster to match the new configuration
>
> This ensures declarative and automated deployments.

### What is image pull policy?
> Image pull policy defines when Kubernetes pulls the container image:
>
> * Always
> * IfNotPresent
> * Never
>
> In production, we typically use versioned tags with IfNotPresent.

### How do you manage multi-environment deployments?
> We manage multiple environments using:
>
> * Separate namespaces (dev, staging, prod)
> * Different values files in Helm
> * Separate Git branches or folders
> * Environment-specific configuration via ConfigMaps and Secrets
>
> In GitOps, each environment usually has its own directory or repo.

👉 “Why GitOps is better than traditional CI/CD?”
> GitOps provides better traceability, auditability, automatic drift detection, and ensures the cluster always matches the declared Git state.