# 🌍 SECTION 3: Terraform State (Very Important)

# 🔹 State Basics

### What is Terraform state file?
Terraform state file stores the mapping between configuration and real infrastructure. It tracks resource IDs and metadata required to manage updates and deletions.

### Why is state file important?
The state file allows Terraform to know what resources exist and their current status. Without it, Terraform cannot manage or update infrastructure properly.

### What is `terraform.tfstate`?
`terraform.tfstate` is the default local state file where Terraform stores infrastructure state in JSON format.

### What is state file structure (JSON)?
The state file is stored in JSON format and contains resource details, dependencies, provider info, and metadata about infrastructure objects.

### What is state drift?
State drift occurs when infrastructure changes are made outside Terraform, causing mismatch between actual infrastructure and state file.

### What is drift detection?
Drift detection identifies differences between real infrastructure and Terraform state during `terraform plan` or `refresh`.

### What is state reconciliation?
State reconciliation updates the state file to reflect actual infrastructure state after detecting drift.

# 🔹 Backends

### What is backend configuration?
Backend configuration defines where and how Terraform stores its state file, such as locally or remotely.

### What is local backend?
Local backend stores the state file on the local machine. It is suitable for small or personal projects.

### What is remote backend?
Remote backend stores the state file in a shared location like S3, Terraform Cloud, or Azure Storage for collaboration.

### Why should we not store state locally in production?
Local state lacks locking, versioning, and team collaboration support. Remote backend ensures security, consistency, and state locking.

### How do you migrate Terraform backend?
We update backend configuration and run `terraform init` again. Terraform prompts to migrate existing state to the new backend.

### What happens when backend configuration changes?
Terraform requires reinitialization using `terraform init`. It may prompt to migrate or reconfigure the state.

# 🔹 State Locking

### What is state locking?
State locking prevents multiple users from modifying the state file simultaneously. It avoids race conditions and corruption.

### What is `-lock=false`?
`-lock=false` disables state locking during execution. It is risky and not recommended in production.

### Two people applied Terraform at same time. What happens?
If state locking is enabled, the second user must wait. Without locking, state corruption or inconsistent infrastructure may occur.

# 🔹 State Commands (Advanced – Very Important)

### What is `terraform state` command?
`terraform state` is used to inspect and manipulate Terraform state without changing infrastructure.

### What is `terraform state list`?
It lists all resources currently tracked in the state file.

### What is `terraform state show`?
It displays detailed information about a specific resource from the state file.

### What is `terraform state mv`?
It moves resources within the state file, useful during refactoring or module restructuring.

### What is `terraform state rm`?
It removes a resource from state without destroying the actual infrastructure.

### How do you move resources between state files?
We use `terraform state mv` or `terraform state pull` and `push` to transfer resources between states safely.

### How do you recover deleted state?
If remote backend with versioning is enabled, we restore from backup. Otherwise, recovery is difficult unless manual recreation is done.

### What happens if state file is corrupted?
Terraform may fail to execute. We restore from backup or remote backend version history.

### What is state backup?
Terraform automatically creates a backup state file before applying changes. Remote backends may also support versioning for recovery.

“What is the most critical Terraform concept?”
> State file and remote backend with locking are the most critical for production environments.