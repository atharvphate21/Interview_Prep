# 🌍 SECTION 2: Terraform Workflow & Commands

# 🔹 Basic Workflow

### What is `terraform init`?
`terraform init` initializes the working directory. It downloads required provider plugins, sets up backend configuration, and prepares the environment for execution.

### What is `terraform plan`?
`terraform plan` creates an execution plan showing what changes Terraform will make. It compares current state with desired configuration without applying changes.

### What is `terraform apply`?
`terraform apply` executes the planned changes to create, update, or delete infrastructure. It updates the state file after successful execution.

### What is `terraform destroy`?
`terraform destroy` removes all resources defined in the configuration. It is mainly used for environment cleanup.

### What is execution plan?
Execution plan is a preview of changes Terraform will apply. It shows resources to be added, modified, or destroyed.

### What happens internally during `terraform apply`?
Terraform refreshes state, builds dependency graph, generates execution plan, and then executes actions in correct order. Finally, it updates the state file.

# 🔹 Validation & Formatting

### What is `terraform validate`?
`terraform validate` checks configuration syntax and internal consistency without accessing remote services.

### What is `terraform fmt`?
`terraform fmt` formats Terraform code according to standard style guidelines. It improves readability and consistency.

# 🔹 State & Refresh

### What is `terraform refresh`?
`terraform refresh` updates the state file with the real-time infrastructure state. It synchronizes Terraform state with actual resources.

### What is drift detection?
Drift detection identifies differences between the actual infrastructure and Terraform state when changes are made outside Terraform.

### What is state reconciliation?
State reconciliation ensures that Terraform state reflects the actual infrastructure after detecting drift or manual changes.

# 🔹 Importing & Targeting

### What is `terraform import`?
`terraform import` brings existing infrastructure into Terraform state without recreating it. It allows Terraform to manage already-created resources.

### What is declarative import block (Terraform 1.x)?
Terraform 1.x introduced declarative import blocks that allow defining imports directly in configuration instead of running CLI commands.

### What is targeted apply?
Targeted apply uses `-target` flag to apply changes to specific resources only. It is useful for debugging but not recommended for regular use.

### What is partial apply?
Partial apply occurs when Terraform applies only part of the planned changes due to errors or targeted execution.

### What is `terraform taint`?
`terraform taint` marks a resource for recreation in the next apply, even if no configuration change is detected.

### What is `terraform untaint`?
`terraform untaint` removes the tainted status from a resource, preventing forced recreation.

# 🔹 Console & Debugging

### What is `terraform console`?
`terraform console` is an interactive shell used to evaluate Terraform expressions and test variable values.

### How do you debug Terraform errors?
I check detailed error messages, use `terraform validate`, enable logging, and verify provider configurations. Reviewing plan output also helps identify issues.

### What is TF_LOG?
`TF_LOG` is an environment variable that enables debug logging in Terraform. It provides detailed execution logs for troubleshooting.

### How do you reduce Terraform execution time?
We can increase parallelism, use remote state efficiently, cache provider plugins, optimize modules, and avoid unnecessary resource recreation.