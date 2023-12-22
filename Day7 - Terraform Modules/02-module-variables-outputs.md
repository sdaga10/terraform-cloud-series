# 7.2. Module Variables and Outputs

In Terraform modules, variables and outputs play a crucial role in defining the interface of the module and providing information to the calling configuration.

## 7.2.1. Module Variables

Variables in a module are used to parameterize the module, allowing users to provide input values when using the module. Here's an example of defining and using variables in a module:

```hcl
# variables.tf

variable "instance_count" {
  description = "The number of instances to create."
  type        = number
  default     = 1
}

variable "instance_type" {
  description = "The type of instances to create."
  type        = string
  default     = "t2.micro"
}
```

In the calling configuration:

```hcl

# main.tf

module "example" {
  source        = "./path/to/module"
  instance_count = 3
  instance_type  = "t3.small"
}
```

## 7.2.2. Module Outputs

Outputs in a module define values that are exposed to the calling configuration. They serve as a way to share information computed within the module. Here's an example of defining and using outputs in a module:

```hcl

# outputs.tf

output "instance_ids" {
  description = "The IDs of the created instances."
  value       = aws_instance.example[*].id
}
```

In the calling configuration:

```hcl

# main.tf

module "example" {
  source = "./path/to/module"
}

output "module_instance_ids" {
  value = module.example.instance_ids
}
```

## 7.2.3. Variable and Output Best Practices

**Documentation:** Provide clear and concise documentation for each variable and output, including descriptions and types.

**Defaults:** Use default values for variables when possible to provide sensible defaults for users.

**Naming:** Follow a consistent naming convention for variables and outputs to enhance readability.

**Explicit Dependencies:** Clearly define dependencies between variables and outputs.

**Testing:** Include tests for modules, especially if they are shared within an organization.

Using variables and outputs effectively enhances the reusability and maintainability of Terraform modules.
