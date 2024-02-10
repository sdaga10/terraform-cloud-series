# 4 variables-and-data-types

In Terraform, variables are used to parameterize your configurations, allowing for flexibility and reusability. They enable you to input values from external sources or dynamically change values based on different use cases. Additionally, Terraform supports various data types that allow you to define the kind of values a variable can hold.

## 4.1.1. Declaring Variables

To declare a variable in Terraform, you use the `variable` block. Here's an example:

```hcl
# Variable Declaration
variable "region" {
  description = "The AWS region where resources will be provisioned."
  type        = string
  default     = "us-west-2"
}
```

In this example:

**Variable Name (region):** A unique identifier for the variable.

**Description:** A human-readable description of the variable's purpose.

**Type (string):** The data type of the variable. It specifies the kind of values the variable can hold.

**Default Value (us-west-2):** An optional default value for the variable.


## 4.1.2. Data Types in Terraform

Terraform supports several data types, including:

**String:** A sequence of characters.

**Number:** Numeric values.

**Bool:** Boolean values (true/false).

**List:** An ordered collection of values.

**Map:** A collection of key-value pairs.

**Object:** A complex data type representing an object with attributes.

Here's an example of using different data types in Terraform for both AWS and Azure :

```
# AWS Variable Example
variable "aws_region" {
  description = "The AWS region where resources will be provisioned."
  type        = string
  default     = "us-west-2"
}

variable "aws_instance_types" {
  description = "List of AWS instance types for a multi-tier application."
  type        = list(string)
  default     = ["t2.micro", "t3.micro"]
}

variable "aws_tags" {
  description = "Tags for AWS resources."
  type        = map(string)
  default     = {
    Name        = "example-instance"
    Environment = "dev"
    Owner       = "terraform"
  }
}

# Azure Variable Example
variable "azure_region" {
  description = "The Azure region where resources will be provisioned."
  type        = string
  default     = "East US"
}

variable "azure_vm_sizes" {
  description = "List of Azure VM sizes for a multi-tier application."
  type        = list(string)
  default     = ["Standard_B1s", "Standard_B2s"]
}

variable "azure_tags" {
  description = "Tags for Azure resources."
  type        = map(string)
  default     = {
    Name        = "example-vm"
    Environment = "dev"
    Owner       = "terraform"
  }
}
```
