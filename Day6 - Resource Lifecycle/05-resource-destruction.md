# 6.5. Resource Destruction

In Terraform, managing the destruction of resources is as important as creating or updating them. This chapter covers how Terraform handles the removal of resources and associated considerations.

## 6.5.1. Destroying Resources

The primary command for destroying resources is `terraform destroy`. This command identifies all resources in the Terraform state and plans their destruction.

```bash
terraform destroy
```

## 6.5.2. Confirming Destruction

When running terraform destroy, Terraform will prompt for confirmation before proceeding. This is a safety measure to prevent accidental destruction of critical resources.

## 6.5.3. Targeted Destruction

If you want to destroy specific resources, you can use the -target flag with terraform destroy. This allows you to selectively destroy resources without affecting others.

```bash
terraform destroy -target=aws_instance.web_server
```

## 6.5.4. Understanding Dependencies

Terraform automatically identifies dependencies between resources and ensures that they are destroyed in the correct order to avoid any conflicts.

## 6.5.5. State Cleanup

After destroying resources, it's essential to clean up the Terraform state. Use the terraform state rm command to remove references to destroyed resources.

```bash
terraform state rm aws_instance.web_server
```

## 6.5.6. Force Destroy

In some cases, Terraform might encounter issues preventing destruction. The -force flag can be used with terraform destroy to forcefully remove resources.

```bash

terraform destroy -force
```

## 6.5.7. State Backup

Before destructive operations, it's advisable to create a backup of the Terraform state. This ensures that you have a snapshot of the infrastructure before making significant changes.

Understanding how Terraform destroys resources is crucial for safely managing the lifecycle of your infrastructure.
