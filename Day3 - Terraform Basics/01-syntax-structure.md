# 3. Terraform Basics: Syntax, Structure, Declaring Resources, and Providers

## 3.1. Syntax and Structure

In Terraform, the configuration language is HashiCorp Configuration Language (HCL). It's designed to be easy to read and write. Let's explore the basic syntax and structure of Terraform configurations.

### Basic Syntax

Terraform configurations use a declarative syntax. Each block represents a resource or a module and contains key-value pairs.

```hcl
# Example Terraform block
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
