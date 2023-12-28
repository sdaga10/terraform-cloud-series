# 7.3. Module Composition and Reusability

Terraform modules are a fundamental building block for creating reusable and shareable components in infrastructure as code (IaC). This chapter explores strategies for composing modules and maximizing their reusability.

## 7.3.1. Module Composition

### Combining Multiple Modules

In Terraform, you can compose modules by including them in other modules. This enables the creation of higher-level abstractions and the organization of infrastructure in a modular and scalable way. Here's an example:

```hcl
# main.tf

module "web_app" {
  source       = "./modules/web_app"
  environment  = "production"
}

module "database" {
  source       = "./modules/database"
  db_name      = module.web_app.db_name
  db_username  = module.web_app.db_username
  db_password  = module.web_app.db_password
}
```

In the example above, the web_app module is included in the main configuration, and its outputs are used as inputs for the database module.

## Parameterized Modules

Make modules more flexible by parameterizing them. Accept input variables for configurable values and outputs for information to be shared. Here's an example:

```hcl
# modules/web_app/main.tf

variable "environment" {
  description = "The environment for the web application."
  type        = string
}

output "db_name" {
  value = var.environment == "production" ? "production_db" : "development_db"
}
```

## 7.3.2. Module Reusability

### Terraform Module Registry

Consider sharing your modules with the community by publishing them to the Terraform Module Registry. This allows others to easily discover and reuse your infrastructure components.

### Module Versioning

When composing modules, use version constraints to specify which versions of a module can be used. This ensures that changes to modules won't unexpectedly affect existing configurations.

```hcl

# main.tf

module "web_app" {
  source  = "organization/web_app/aws"
  version = "~> 1.0"
}
```

## 7.3.3. Best Practices

**Modular Design:** Break down infrastructure into small, focused modules.

**Standard Interfaces:** Define clear input and output variables for modules.

**Documentation:** Provide detailed documentation for module usage.

**Testing:** Include tests for modules to ensure reliability.

**Semantic Versioning:** Follow semantic versioning for module releases.

By mastering module composition and reusability, you can build a scalable and maintainable infrastructure with Terraform.

