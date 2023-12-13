# 5.3. Variable Files and Environments

Variable files and environments in Terraform provide mechanisms to manage configurations for different environments (e.g., development, staging, production) and allow you to parameterize your deployments more effectively.

## 5.3.1. Variable Files

Variable files are used to define values for your input variables outside of your main Terraform configuration. This separation enables you to maintain different sets of configurations for different environments.

### Structure of a Variable File

A variable file typically has a `.tfvars` extension and contains key-value pairs for your input variables.

#### Example Variable File (vars-dev.tfvars)

```hcl
aws_region          = "us-west-2"
aws_instance_type   = "t3.micro"
azure_location      = "West US"
azure_vm_size       = "Standard_B2s"
```
5.3.2. Environments
Environments in Terraform represent different deployment scenarios or stages (e.g., development, staging, production). By organizing your configurations based on environments, you can maintain consistency and adapt settings for specific contexts.

Directory Structure for Environments
```lua
|-- environments/
|   |-- dev/
|       |-- main.tf
|       |-- vars-dev.tfvars
|   |-- prod/
|       |-- main.tf
|       |-- vars-prod.tfvars
```

Using Variable Files in Environments
In each environment's main.tf file, you reference the corresponding variable file.

Example Environment Configuration (dev/main.tf)

```hcl

provider "aws" {
  region = var.aws_region
}

provider "azurerm" {
  features = {}
  region   = var.azure_location
}

variable "aws_region" {}
variable "aws_instance_type" {}
variable "azure_location" {}
variable "azure_vm_size" {}

# Other resource configurations...
```

5.3.3. Running Terraform with Variable Files
When running Terraform commands, you specify the variable file for the targeted environment.

```bash
terraform apply -var-file=environments/dev/vars-dev.tfvars
```

This allows you to seamlessly manage configurations for different environments using variable files and organized directory structures.

