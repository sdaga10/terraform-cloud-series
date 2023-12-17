# 6.3. Resource Modification and Updates

Modifying and updating resources in Terraform is a common scenario as infrastructure requirements evolve. Understanding how Terraform handles these modifications is crucial for maintaining a desired infrastructure state.

## 6.3.1. Modifying Resource Configurations

To modify a resource's configuration, you can update the respective resource block in your Terraform configuration file. After making changes, run `terraform plan` to see the planned modifications.

```hcl
# Before modification
resource "aws_instance" "example_instance" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}

```hcl
# After modification
resource "aws_instance" "example_instance" {
  ami           = "ami-abc12345"
  instance_type = "t3.micro"
}
```

## 6.3.2. Planning Modifications

Use terraform plan to see the planned modifications before applying them. This command provides an overview of what Terraform will change in the infrastructure.

```bash
terraform plan
```

## 6.3.3. Applying Modifications

Apply modifications using terraform apply. Terraform will prompt for confirmation before making any changes to the infrastructure.

```hcl
terraform apply
```

## 6.3.4. Rolling Back Modifications

If there are issues during the apply phase, Terraform allows rolling back changes. The command terraform apply -refresh-only can be used to refresh the state without applying modifications.

```bash
terraform apply -refresh-only
```

## 6.3.5. Handling State Changes

Terraform manages state changes by tracking the previous and current states. It identifies what needs to be added, modified, or deleted to bring the infrastructure to the desired state.

## 6.3.6. Versioning and State

Terraform state should be versioned and stored securely. This helps in tracking changes over time and collaborating with other team members.

Understanding the process of modifying and updating resources is essential for efficiently managing infrastructure using Terraform.
