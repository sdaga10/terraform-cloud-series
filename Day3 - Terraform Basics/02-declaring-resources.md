## 3.2. Declaring Resources in Terraform

In Terraform, the primary purpose is to define and provision infrastructure resources. Resources are entities such as compute instances, storage buckets, databases, etc. Let's explore how to declare resources in Terraform.

```hcl
# Resource Declaration
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```
Here's a breakdown of the elements in the resource declaration:

Resource Type (aws_instance): Specifies the type of resource to create. In this example, it's an AWS EC2 instance.

Resource Name (example): A local name for the resource instance. You'll refer to this name when interacting with the resource in other parts of your configuration.

Resource Configuration: Key-value pairs that define the configuration of the resource. In this case, it specifies the Amazon Machine Image (AMI) and the instance type.

This declaration instructs Terraform to create an AWS EC2 instance using the specified AMI and instance type. As you progress, you'll work with various types of resources and configurations to model your infrastructure.

Understanding how to declare resources is fundamental to building Terraform configurations. In the subsequent sections, we'll explore more about providers, variables, and delve into advanced features of the HashiCorp Configuration Language (HCL).
