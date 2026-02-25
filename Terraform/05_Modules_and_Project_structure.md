# 🌍 SECTION 5: Modules & Project Structure

# 🔹 Module Basics

### What is a module in Terraform?
> A module is a reusable container of Terraform configuration files. It helps organize infrastructure and promote code reuse.

### What is root module?
> The root module is the main Terraform configuration directory where execution starts. It can call other child modules.

### What is child module?
> A child module is a reusable module called by the root module or another module to encapsulate specific infrastructure components.

### How do you call a module?
> A module is called using the `module` block with a source path and input variables.
> 
> Example:
> 
> ```id="l9h2kq"
> module "vpc" {
>   source = "./modules/vpc"
> }
> ```

### What is module source?
> Module source defines where the module code is located, such as local path, Git repository, or Terraform Registry.

### How do you version modules?
> Modules are versioned using Git tags or version constraints in Terraform Registry to ensure stable and controlled deployments.

### How do you structure Terraform project?
> A typical structure includes separate folders for modules, environments (dev/prod), backend configuration, and variables for better maintainability.

### How to reuse code using modules?
> We create reusable modules for components like VPC, IAM, or EKS and call them with different inputs for different environments.

### What are best practices for modules?
> Keep modules small and focused, define clear inputs and outputs, version modules properly, and avoid hardcoding values.

# 🔹 Advanced Module Concepts

### What are `depends_on` for modules?
> `depends_on` ensures one module executes after another when implicit dependencies are not automatically detected.

### What is moved block (Terraform 1.x)?
> The `moved` block helps refactor or rename resources without recreating them by updating state mappings safely.

### How do you refactor Terraform code safely?
> Use `terraform state mv` or `moved` blocks to relocate resources in state before changing configuration structure.

### How do you split large state files?
> We split infrastructure into multiple smaller Terraform projects or use separate backends to reduce risk and improve performance.

### Monorepo vs multi-repo for Terraform?
> Monorepo keeps all infrastructure code in one repository for easier management. Multi-repo separates environments or services for better isolation and access control.

“Why use modules in production?”
> Modules improve reusability, maintainability, version control, and reduce duplication across environments.