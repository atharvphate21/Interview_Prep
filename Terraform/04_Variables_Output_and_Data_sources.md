# 🌍 SECTION 4: Variables, Outputs & Data Sources

# 🔹 Variables

### What are variables in Terraform?
Variables are placeholders used to parameterize Terraform configurations. They make code reusable and allow dynamic input values.

### Types of variables?
Terraform supports string, number, bool, list, map, object, and tuple types. These help define structured and validated input values.

### What is variable precedence?
Variable values are loaded in order of priority: CLI flags → `.tfvars` files → environment variables → default values in configuration.

### What is `terraform.tfvars`?
`terraform.tfvars` is a file used to define variable values automatically loaded by Terraform during execution.

### What are environment variables in Terraform?
Terraform allows variables to be set using environment variables prefixed with `TF_VAR_`.

Example:

```
export TF_VAR_region=us-east-1
```

### How do you pass environment variables to Terraform?
We use `TF_VAR_variable_name` format to pass environment variables, and Terraform automatically reads them.

### What is sensitive variable?
Sensitive variables are marked with `sensitive = true` to prevent them from being displayed in CLI output, such as passwords or API keys.

### What is optional variable type (Terraform 1.x)?
Terraform 1.x introduced optional object attributes, allowing flexible input structures without requiring all fields to be defined.

# 🔹 Outputs & Locals

### What is output in Terraform?
Outputs expose values from Terraform configuration, such as resource IDs or IP addresses, for use outside Terraform or by other modules.

### What is local variable?
Local variables simplify complex expressions and avoid repetition. They are defined inside a `locals` block.

### What are precondition and postcondition blocks?
Preconditions validate input or resource configuration before execution. Postconditions validate results after resource creation.

# 🔹 Data Sources

### What is data source?
Data sources allow Terraform to fetch existing infrastructure information without creating new resources.

### Difference between resource and data source?
Resource creates and manages infrastructure. Data source only reads existing infrastructure data.

### When would you use data source instead of resource?
We use data sources when referencing existing infrastructure like VPCs, AMIs, or IAM roles instead of creating new ones.

“Why are data sources important?”
> They help integrate Terraform with existing infrastructure without duplicating resources.