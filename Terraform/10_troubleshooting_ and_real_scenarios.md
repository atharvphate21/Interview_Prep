# 🌍 SECTION 10: Troubleshooting & Real Scenarios

### Terraform plan shows changes but nothing changed. Why?
This usually happens due to **drift**, **provider schema changes**, non-deterministic attributes (like timestamps), or differences in computed values. I run `terraform refresh`/plan again and check which attributes are forcing changes.

### Terraform apply failed halfway. What happens?
Terraform may have created/updated some resources before failing, and state is updated for whatever succeeded. Next `terraform apply` will continue from the current state; I review the error, fix it, and re-apply.

### How do you detect drift?
I detect drift using `terraform plan` (and sometimes `terraform refresh`) to compare real infrastructure with state. In teams, we run scheduled plans in CI to catch drift early.

### State file corrupted. What will you do?
I restore from **remote backend versioning** or the latest **state backup**. If no backup exists, I re-import critical resources and rebuild state carefully.

### Two people applied Terraform at same time. What happens?
With remote backend + locking (e.g., S3 + DynamoDB), the second apply is blocked until the lock is released. Without locking, it can cause state corruption and inconsistent infrastructure.

### How do you reduce plan time?
I reduce plan time by splitting large projects into smaller states/modules, limiting data source calls, enabling plugin cache, and improving provider/API performance. Avoiding unnecessary refresh and using targeted runs only for debugging also helps.

### How do you migrate Terraform backend?
I update the backend config and run `terraform init -migrate-state`. Terraform moves the existing state to the new backend after confirmation.

### How do you refactor Terraform safely in production?
I refactor using `moved` blocks (Terraform 1.x) or `terraform state mv` so resources don’t get recreated. I do it via PR + plan review, and apply through CI with locking enabled.

### What happens if real infrastructure is manually modified?
That creates **drift**—Terraform will detect differences in the next plan and may try to revert or adjust resources. Best practice is to avoid manual changes or import/update Terraform config accordingly.

### How do you recover accidentally deleted resources?
If Terraform manages it, I run `terraform apply` to recreate it. If it’s state-only deletion, I restore state or re-import; if the resource is truly deleted, I recreate and validate dependencies.

### How do you troubleshoot provider version conflicts?
I check `required_providers` constraints and the `.terraform.lock.hcl` file, then run `terraform init -upgrade` or pin compatible versions. In CI, I keep versions fixed to avoid unexpected upgrades.