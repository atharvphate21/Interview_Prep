# 🌍 SECTION 8: Security & Policy as Code

### How do you secure Terraform state?
We store state in a remote backend like S3 with encryption enabled and DynamoDB for locking. Access is restricted using IAM policies and versioning is enabled for recovery.

### How do you handle secrets in Terraform?
We avoid hardcoding secrets in `.tf` files and use environment variables, secret managers, or Vault. Sensitive variables are marked with `sensitive = true`.

### How do you manage secrets using HashiCorp Vault?
Terraform integrates with Vault using the Vault provider to fetch secrets dynamically. This avoids storing credentials in state or code.

### How do you restrict provider versions?
We define version constraints in the `required_providers` block to avoid unexpected breaking changes during provider upgrades.

### How do you scan Terraform code for vulnerabilities?
We use static analysis tools like tfsec or Checkov in CI pipelines to detect misconfigurations and security risks before apply.

### What is tfsec?
tfsec is a static analysis tool that scans Terraform code for security issues and misconfigurations.

### What is Checkov?
Checkov is an infrastructure security scanner that checks Terraform, CloudFormation, and Kubernetes configs against security best practices.

### What is policy as code?
Policy as Code means defining compliance and governance rules in code form, which are automatically enforced during infrastructure deployment.

### What is Sentinel?
Sentinel is HashiCorp’s policy as code framework used in Terraform Cloud/Enterprise to enforce governance and compliance rules.

### How do you enforce tagging policies?
We enforce tagging using policy as code tools like Sentinel or OPA, or by using required variables and validation blocks in modules.

If asked “How do you secure Terraform in production?”
> Remote encrypted backend, restricted IAM access, secret manager integration, provider version locking, and policy enforcement in CI.