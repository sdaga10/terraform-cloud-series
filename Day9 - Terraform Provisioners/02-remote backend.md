# 02. Remote Backend

## Introduction

When working with Terraform, using a remote backend is essential for collaboration and state management. Remote backends store the Terraform state file in a centralized location, enabling multiple users to work on the same infrastructure.

In this chapter, we'll explore how to configure remote backends with examples for both AWS and Azure.

## 1. AWS S3 Remote Backend

### Configuration

To configure a remote backend using AWS S3, create a new file named `backend.tf` and add the following content:

```hcl
terraform {
  backend "s3" {
    bucket         = "your-s3-bucket-name"
    key            = "path/to/your/state-file.tfstate"
    region         = "your-aws-region"
    encrypt        = true
    dynamodb_table = "your-dynamodb-lock-table"
  }
}
```

Replace the placeholder values with your specific information. The dynamodb_table configuration is used for state locking.

### Usage

Initialize Terraform with the configured backend:

```hcl
terraform init
```

## 2. Azure Storage Account Remote Backend

### Configuration

For Azure, create a backend.tf file with the following content:

```hcl
terraform {
  backend "azurerm" {
    resource_group_name   = "your-resource-group"
    storage_account_name  = "your-storage-account"
    container_name        = "your-container"
    key                   = "path/to/your/state-file.tfstate"
    subscription_id       = "your-subscription-id"
  }
}
```

Replace the placeholder values with your Azure-specific information.

### Usage

Initialize Terraform as follows:

```hcl
terraform init
```
