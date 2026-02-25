# 🌍 SECTION 7: Terraform in CI/CD & DevOps

# 🔹 CI/CD Integration

### How does Terraform integrate with CI/CD?
Terraform is executed inside pipelines where `init`, `plan`, and `apply` are automated. Code changes trigger pipeline runs, ensuring infrastructure changes are reviewed and applied safely.

### How do you implement Terraform in GitOps model?
In GitOps, Terraform code is stored in Git and changes are applied through pull requests. The CI pipeline runs `plan` and applies changes only after approval.

### How do you implement plan approval workflow?
The pipeline runs `terraform plan` and posts output for review. After manual approval in PR or pipeline stage, `terraform apply` is executed.

### How do you store plan files?
We generate plan files using `terraform plan -out=tfplan` and store them as pipeline artifacts to ensure the exact approved plan is applied.

### How do you prevent direct apply from local machines?
We restrict access by using remote backends, enforcing IAM permissions, and allowing apply only through CI pipelines or Terraform Cloud.

# 🔹 Integration with Tools

### How do you integrate Terraform with Jenkins?
Jenkins pipelines execute Terraform stages using shell steps. Credentials are stored securely, and remote state is configured for team collaboration.

### How do you integrate Terraform with GitHub Actions?
GitHub Actions workflow runs Terraform commands using official Terraform setup actions. Secrets are stored in GitHub Secrets.

### How do you integrate Terraform with GitLab CI?
GitLab CI pipelines define stages for init, plan, and apply. Plan output can be shown in merge requests before approval.

# 🔹 Team Collaboration

### How do you handle Terraform in team environments?
We use remote backend with state locking, version control with PR reviews, and CI pipelines to ensure controlled and collaborative changes.

### How do you handle large Terraform projects?
We break infrastructure into modules and separate state files. Each environment or service has its own backend to reduce risk and complexity.

### How do you implement RBAC in Terraform Cloud?
Terraform Cloud provides role-based access control at organization, workspace, and team levels. We assign permissions like plan-only or apply access.

If asked “What is the safest production Terraform setup?”
> Remote backend with state locking, PR-based plan approval, and apply only through CI/CD.