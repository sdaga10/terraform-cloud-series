# 6.1. Resource Declaration and Configuration

In Terraform, resources represent infrastructure components such as virtual machines, networks, databases, etc. Declaring and configuring resources is a fundamental aspect of defining your infrastructure using Terraform.

## 6.1.1. Declaring Resources

Resources are declared using the `resource` block in your Terraform configuration. Each resource block specifies the type of resource and defines its characteristics.

### AWS Example

```hcl
resource "aws_instance" "example_instance" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```

### Azure Example

```hcl

resource "azurerm_virtual_machine" "example_vm" {
  name                  = "example-vm"
  resource_group_name   = "example-rg"
  location              = "East US"
  vm_size               = "Standard_B1s"
  # Other configuration settings...
}
```

## 6.1.2. Resource Configuration Settings

Each resource has specific configuration settings based on the type of infrastructure it represents. These settings are provided within the respective resource block.

### Common Configuration Settings

**name:** A user-defined name for the resource.
**resource_group_name (Azure):** The name of the resource group the resource belongs to.
**ami (AWS):** The ID of the Amazon Machine Image for an EC2 instance.
**instance_type (AWS):** The type of EC2 instance.

## 6.1.3. Organizing Resources

It's common to organize related resources within modules or by using naming conventions. This enhances readability and maintainability of your Terraform configurations.

## Module Example
```
hcl

module "example_module" {
  source = "./modules/example"

  # Module-specific configurations...
}
```

## 6.1.4. Dependencies Between Resources

Terraform automatically manages dependencies between resources, ensuring that resources are created and destroyed in the correct order based on their dependencies.

Understanding how to declare and configure resources is crucial for effectively defining your infrastructure using Terraform.
