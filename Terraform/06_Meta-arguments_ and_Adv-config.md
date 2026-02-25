# 🌍 SECTION 6: Meta-Arguments & Advanced Configuration

### What is lifecycle block?
The `lifecycle` block controls resource behavior during creation and updates. It includes options like `create_before_destroy`, `prevent_destroy`, and `ignore_changes`.

### What is depends_on?
`depends_on` explicitly defines resource dependencies when Terraform cannot detect them automatically. It ensures correct creation order.

### What is count?
`count` creates multiple instances of a resource based on a number. It is index-based and useful for simple replication.

### What is for_each?
`for_each` creates multiple resources using a map or set of values. It is key-based and better for managing unique resource instances.

### Difference between count and for_each?
`count` uses numeric indexing and may cause recreation if order changes.
`for_each` uses keys, making it more stable for dynamic infrastructure.

### What is dynamic block?
Dynamic block is used to generate nested configuration blocks programmatically within a resource using loops.

### What is null resource?
`null_resource` is a placeholder resource used to trigger provisioners or custom actions without managing real infrastructure.

### What is provisioner?
Provisioners execute scripts or commands during resource creation or destruction. They are used for bootstrapping or configuration tasks.

### Types of provisioners?
The main types are `local-exec`, `remote-exec`, and file provisioner. They execute commands locally or remotely.

### Why are provisioners discouraged?
Provisioners are not idempotent and break Terraform’s declarative model. They should be avoided in favor of configuration management tools.

### What is remote-exec?
`remote-exec` runs commands on a remote machine after it is created, typically via SSH or WinRM.

### What is local-exec?
`local-exec` runs commands on the local machine where Terraform is executed.

### What is Terraform workspace?
Workspace allows managing multiple state files within the same configuration, commonly used for separating environments like dev and prod.

### How do you manage multiple environments in Terraform?
We manage environments using separate workspaces, separate backend configurations, or different variable files for dev, staging, and production.

“When to use count vs for_each?”
> Use count for simple numeric scaling, and for_each when managing resources with unique identifiers.