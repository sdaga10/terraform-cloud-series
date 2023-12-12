# 5. Input Variables

Input variables in Terraform allow you to parameterize your configurations, making them more flexible and reusable. With input variables, you can customize the behavior of your Terraform modules and configurations without modifying the source code.

## 5.1. Input Variables

Input variables are defined within your Terraform configuration to receive values from the calling module or environment. These variables act as parameters, allowing you to dynamically adjust settings in your infrastructure deployments.

### Declaring Input Variables

In Terraform, you declare input variables using the `variable` block. Each variable has a name, a type, and an optional default value.

#### AWS Example

```hcl
variable "aws_region" {
  description = "The AWS region where resources will be provisioned."
  type        = string
  default     = "us-east-1"
}

variable "aws_instance_type" {
  description = "The type of EC2 instance to launch in AWS."
  type        = string
  default     = "t2.micro"
}
```

#### Azure Example
```hcl
variable "azure_location" {
  description = "The Azure region where resources will be provisioned."
  type        = string
  default     = "East US"
}

variable "azure_vm_size" {
  description = "The size of the Azure virtual machine."
  type        = string
  default     = "Standard_B1s"
}
```

## 5.2. Using Input Variables

Once declared, input variables can be utilized in your Terraform configurations.

### Using Input Variables in Resource Configuration

## AWS Example

```hcl
resource "aws_instance" "example_instance" {
  ami           = "ami-12345678"
  instance_type = var.aws_instance_type
  region        = var.aws_region
}
```

## Azure Example

```hcl
resource "azurerm_virtual_machine" "example_vm" {
  name                  = "example-vm"
  location              = var.azure_location
  size                  = var.azure_vm_size
  resource_group_name   = "example-resource-group"
  admin_username        = "adminuser"
  admin_password        = "Password1234!"
  # Other Azure VM settings...
}
```

In these examples, input variables allow you to parameterize your resource configurations, providing flexibility and reusability in your Terraform code.
