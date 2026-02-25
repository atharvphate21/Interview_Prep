# 🌍 SECTION 1: Terraform Fundamentals

## 🔹 Core Basics

### What is Terraform?
Terraform is an open-source Infrastructure as Code tool by HashiCorp used to provision and manage infrastructure declaratively. It supports multiple cloud providers and enables automated, repeatable deployments.

### What is Infrastructure as Code (IaC)?
Infrastructure as Code means managing infrastructure using code instead of manual processes. It ensures automation, version control, consistency, and faster provisioning.

### Why do we use Terraform?
We use Terraform to automate infrastructure creation, manage multi-cloud environments, and maintain consistency across environments. It also provides state management and dependency handling.

### What problem does Terraform solve?
Terraform eliminates manual infrastructure provisioning, reduces configuration drift, and enables version-controlled, repeatable deployments across environments.

### What is declarative vs imperative approach?
Declarative defines the desired end state, and the system figures out how to achieve it. Imperative defines step-by-step instructions to reach the goal. Terraform follows the declarative model.

### Difference between mutable vs immutable infrastructure?
Mutable infrastructure updates resources in place, while immutable infrastructure replaces resources entirely during changes. Immutable is more predictable and reduces configuration drift.

### What is idempotency in Terraform?
Idempotency means applying the same configuration multiple times results in the same infrastructure state without unintended changes.

# 🔹 Architecture & Internals

### What is Terraform architecture?
Terraform consists of Terraform Core, Provider plugins, and the State file. Core builds execution plans, providers interact with APIs, and state tracks resource mappings.

### What are Terraform Core and Provider plugins?
Terraform Core reads configuration files, builds the dependency graph, and manages state. Provider plugins interact with external APIs like AWS or Azure to create resources.

### How do provider plugins communicate with Terraform Core?
They communicate via RPC (Remote Procedure Calls) using gRPC. Terraform Core sends requests, and providers execute them against cloud APIs.

### What is DAG (Directed Acyclic Graph)?
DAG represents resource dependencies in Terraform. It ensures resources are created, updated, or destroyed in the correct order without circular dependencies.

### How does Terraform build dependency graph?
Terraform analyzes references between resources automatically. It also considers explicit dependencies defined using `depends_on`.

### How does dependency resolution work?
Terraform determines resource order based on implicit and explicit dependencies. Independent resources are created in parallel, dependent ones sequentially.

### How does parallelism work in Terraform?
Terraform creates resources in parallel when there are no dependencies between them. This improves execution speed and efficiency.

### What is `-parallelism` flag?
The `-parallelism` flag controls the number of concurrent operations during apply or destroy. It helps manage API rate limits and performance.

### What is Terraform graph command?
`terraform graph` generates a visual representation of the dependency graph in DOT format, useful for debugging dependencies.

### What is provider plugin?
A provider plugin is a binary that interacts with specific cloud or service APIs to manage infrastructure resources.

### What is plugin cache?
Plugin cache stores downloaded provider binaries locally, reducing repeated downloads and improving initialization speed.

### What is multi-provider configuration?
Multi-provider configuration allows using multiple cloud providers within a single Terraform project, such as AWS and Kubernetes together.

### What is provider alias?
Provider alias allows defining multiple configurations of the same provider, such as multiple AWS regions in one setup.

# 🔹 Terraform Ecosystem

### What is Terraform CLI?
Terraform CLI is the command-line interface used to run commands like init, plan, apply, and destroy for managing infrastructure.

### What is Terraform Registry?
Terraform Registry is a public repository of providers and reusable modules that simplifies infrastructure development.

### What is module registry?
Module registry stores reusable Terraform modules that follow best practices and standardize infrastructure patterns.

### What is Terraform Cloud?
Terraform Cloud is a managed service that provides remote state management, collaboration features, and CI/CD integration.

### What is Terraform Enterprise?
Terraform Enterprise is the self-hosted version of Terraform Cloud designed for enterprises requiring strict security and compliance.

### Difference between Terraform Cloud and Enterprise?
Terraform Cloud is SaaS and fully managed by HashiCorp. Terraform Enterprise is self-hosted and suitable for regulated environments.

### Difference between Terraform and CloudFormation?
Terraform supports multi-cloud environments and uses HCL language. CloudFormation is AWS-specific and tightly integrated with AWS services.

### Difference between Terraform and OpenTofu?
OpenTofu is a community-driven fork of Terraform. Terraform is maintained by HashiCorp under BSL license, while OpenTofu remains fully open-source.

### Why did OpenTofu fork from Terraform?
OpenTofu was forked after HashiCorp changed Terraform’s license to BSL. The community wanted to maintain an open-source alternative.