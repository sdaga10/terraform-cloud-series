# 2.2. Basic Terraform Commands

Terraform provides a set of commands that allow you to interact with and manage your infrastructure. In this section, we'll cover some of the basic Terraform commands you'll frequently use.

## Initializing a Terraform Configuration

Before you can apply or plan changes to your infrastructure, you need to initialize your Terraform configuration. Use the following command:

```bash
terraform init

This command downloads the necessary providers and sets up the working directory.

Creating an Execution Plan
To see what changes Terraform will apply to your infrastructure, you can create an execution plan using:

terraform plan

This command analyzes your configuration and generates an execution plan, which outlines the changes Terraform will make.

Applying Changes
Once you're satisfied with the execution plan, you can apply the changes to your infrastructure:

terraform apply

Viewing Resource State
To view the current state of your Terraform-managed infrastructure, use:

terraform show

This command provides a human-readable output of the current resource state.

Destroying Resources
If you want to destroy the resources defined in your configuration, use:

terraform destroy

Terraform will prompt you to confirm the destruction of resources.

Conclusion
These are some of the fundamental Terraform commands to get you started. As you work with Terraform, you'll discover additional commands and options to suit your infrastructure management needs.



