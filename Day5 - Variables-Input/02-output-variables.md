# 5.2. Output Variables

Output variables in Terraform allow you to expose certain values from your configuration so that they can be easily consumed by other modules or external systems.

## 5.2.1. Declaring Output Variables

Output variables are declared using the `output` block in your Terraform configuration. They specify which values you want to expose.

### AWS Example

```hcl
output "aws_instance_public_ip" {
  description = "Public IP address of the AWS EC2 instance"
  value       = aws_instance.example_instance.public_ip
}
```

### Azure Example

```hcl
output "azure_vm_public_ip" {
  description = "Public IP address of the Azure virtual machine"
  value       = azurerm_virtual_machine.example_vm.public_ip_address
}
```
## 5.2.2. Using Output Variables

Output variables can be referenced in other Terraform configurations or accessed via the Terraform CLI.

### Using Output Variables

```hcl
module "example" {
  source = "./example-module"

  # Other module configurations...

  aws_instance_public_ip = aws_instance.example_instance.public_ip
  azure_vm_public_ip     = azurerm_virtual_machine.example_vm.public_ip_address
}
```
In this example, the aws_instance_public_ip and azure_vm_public_ip output variables from the respective modules are referenced in another module.

Output variables provide a way to share information between different parts of your Terraform configuration or with external systems.
