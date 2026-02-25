# 🌍 SECTION 9: Cloud-Specific Terraform (AWS Focused)

# 🔹 Networking & IAM
### How do you create VPC using Terraform?
We define `aws_vpc`, subnets, route tables, and internet gateway resources in configuration. For production, we typically use reusable VPC modules instead of writing everything from scratch.

### How do you manage IAM using Terraform?
We create IAM roles, policies, and attachments using Terraform resources. IAM policies are usually defined in JSON format or using `aws_iam_policy_document`.

### How do you structure multi-account architecture?
We use separate AWS accounts for dev, staging, and production. Terraform uses assume_role to access different accounts securely.

### How do you use assume_role in provider?
We configure the AWS provider with an `assume_role` block to assume a specific IAM role in another account for secure cross-account access.

### How do you manage cross-account resources?
We use IAM roles with trust relationships and configure provider aliases for each account to manage resources securely.

# 🔹 Remote Backend in AWS

### How do you configure remote backend in Amazon S3?
We define backend configuration with S3 bucket, key path, region, and enable DynamoDB table for state locking.

### What is Amazon DynamoDB locking?
DynamoDB is used to implement state locking when using S3 backend. It prevents multiple users from applying Terraform at the same time.

# 🔹 Kubernetes & Containers

### How do you manage Kubernetes cluster using Terraform?
We use Terraform AWS provider to create infrastructure and Kubernetes provider to manage cluster resources like namespaces and deployments.

### What is Terraform provider for Kubernetes?
The Kubernetes provider allows Terraform to manage Kubernetes resources like Pods, Services, and ConfigMaps after the cluster is created.

### How do you deploy EKS using Terraform?
We create VPC, IAM roles, and EKS cluster resources. In production, we usually use official EKS modules for best practices.

### How do you manage EKS add-ons?
EKS add-ons like CoreDNS or VPC CNI are managed using Terraform resources or AWS EKS add-on configurations.

### How do you manage infrastructure for Amazon EKS?
We separate networking, cluster, and node groups into modules. We also manage IAM roles and security groups carefully for production readiness.

# 🔹 Advanced Cloud Topics

### How do you handle multi-region infrastructure?
We use provider aliases for different regions and define region-specific resources. Remote state is usually separated per region.

### How do you import existing AWS resources?
We use `terraform import` to bring existing AWS resources into Terraform state without recreating them.

### How do you implement blue-green infrastructure?
We provision parallel infrastructure environments and switch traffic using load balancers or DNS updates.

### How do you rollback infrastructure changes?
We revert code changes in Git and reapply Terraform. Remote backend versioning helps restore previous state if needed.

If asked “What is the safest AWS Terraform setup?”
> Remote S3 backend with encryption, DynamoDB locking, assume_role for cross-account access, and CI-based plan approval workflow.