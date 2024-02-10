# Chapter 11.2: Dynamic Blocks

Dynamic blocks in Terraform allow you to define repeating configurations dynamically based on data structures. This powerful feature enables you to create flexible and reusable configurations, especially when dealing with variable numbers of similar resources or configurations.

## Understanding Dynamic Blocks

Dynamic blocks are used to generate multiple instances of a block within a configuration based on a collection or map of data. This means you can dynamically create resources, variables, or other configurations based on the elements of a list, set, map, or other data structures.

### Syntax

The syntax for dynamic blocks consists of the `dynamic` keyword followed by a block type and an expression that evaluates to a list, set, or map. Within the dynamic block, you define the configuration that will be repeated for each element in the evaluated data structure.

Here's a basic example of the syntax:

```hcl
dynamic "block_type" {
  for_each = var.list_of_objects
  content {
    # Configuration to be repeated for each object in the list
  }
}
```

## Use Cases
Dynamic blocks are particularly useful in scenarios where you need to generate multiple similar configurations without repeating the same block multiple times in your code. Some common use cases include:

Creating multiple instances of resources based on a list of input parameters.
Generating dynamic variable definitions based on environment-specific configurations.
Managing conditional configurations based on the elements of a map or list.

## AWS Example

Let's consider a scenario where you need to create multiple AWS S3 buckets based on a list of bucket names defined in a variable. Instead of manually defining each bucket configuration, you can use dynamic blocks to generate the configurations dynamically.

```hcl
variable "bucket_names" {
  type    = list(string)
  default = ["bucket1", "bucket2", "bucket3"]
}

resource "aws_s3_bucket" "example" {
  dynamic "bucket" {
    for_each = var.bucket_names
    content {
      bucket = bucket.value
      # Additional bucket configurations
    }
  }
}
```
## Azure Example

Similarly, in Azure, you can use dynamic blocks to dynamically create multiple instances of resources. For example, let's say you need to create multiple Azure storage accounts based on a list of account names:

```hcl

variable "account_names" {
  type    = list(string)
  default = ["account1", "account2", "account3"]
}

resource "azurerm_storage_account" "example" {
  dynamic "account" {
    for_each = var.account_names
    content {
      name                     = account.value
      resource_group_name      = azurerm_resource_group.example.name
      location                 = azurerm_resource_group.example.location
      account_tier             = "Standard"
      account_replication_type = "LRS"
    }
  }
}

```

In this example, the azurerm_storage_account resource dynamically generates multiple storage account configurations based on the elements of the account_names variable.

### Conclusion

Dynamic blocks provide a flexible and efficient way to generate repeating configurations in Terraform based on data structures. By leveraging dynamic blocks, you can write cleaner, more maintainable code and automate the creation of resources based on dynamic input parameters.
