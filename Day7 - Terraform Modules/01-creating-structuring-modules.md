# 7.1. Creating and Structuring Modules

In Terraform, modules are a way to organize and package your Terraform configurations into reusable components. This chapter explores the creation and structuring of Terraform modules.

## 7.1.1. What are Modules?

A module in Terraform is a collection of Terraform files grouped together in a directory. It can include resource definitions, input variables, output variables, and other Terraform configurations. Modules enable code reuse and help organize infrastructure components.

## 7.1.2. Module Structure

A typical module structure includes the following elements:

```plaintext
module/
│
├── main.tf          # Main configuration file defining resources
├── variables.tf     # Input variable definitions
├── outputs.tf       # Output variable definitions
├── README.md        # Documentation for the module
├── examples/        # Examples demonstrating module usage
│   └── example1.tf
│   └── example2.tf
│
├── nested_module/   # Nested modules, if applicable
│   └── main.tf
│   └── variables.tf
│   └── outputs.tf
│
└── tests/           # Tests for the module
    └── test_module.tf
```

## 7.1.3. Module Usage
To use a module in another Terraform configuration, you can reference it using the module block in your main configuration file.

```hcl

module "example" {
  source = "./path/to/module"
  # input variables
  var1 = "value1"
  var2 = "value2"
}

output "module_output" {
  value = module.example.output_variable
}
```

## 7.1.4. Module Versioning

It's a good practice to version your modules to ensure consistent usage. You can use version constraints in the source argument to specify which version of the module to use.

```hcl

module "example" {
  source = "git::https://github.com/example/module.git?ref=v1.2.0"
  # input variables
  var1 = "value1"
  var2 = "value2"
}
```

## 7.1.5. Module Registry
You can share modules with the Terraform community by publishing them to the Terraform Module Registry. This makes it easy for others to discover and use your modules.

Creating well-structured and versioned modules enhances code maintainability and promotes collaboration within your organization and the broader Terraform community.
