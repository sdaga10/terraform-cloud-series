# 10.1. Sentinel Policies

## Introduction

Sentinel is a policy as code framework developed by HashiCorp. In the context of Terraform, Sentinel allows you to define and enforce policies to control how infrastructure resources are provisioned. These policies act as a safety net, ensuring that infrastructure changes align with organizational requirements and compliance standards.

## Key Concepts

### Policy Language

Sentinel uses its own policy language to express rules and constraints. The language is designed to be human-readable and allows you to define conditions, constraints, and actions.

### Policy Sets

Policies are organized into sets, allowing you to group related policies together. Policy sets can be associated with specific workspaces or applied globally.

### Enforcement Levels

Sentinel supports different enforcement levels for policies, such as advisory, soft-mandatory, and hard-mandatory. These levels determine the impact of policy violations on Terraform operations.

## Creating Sentinel Policies

To create a Sentinel policy, follow these steps:

1. **Policy Definition:**
   Define your policy in the Sentinel language. For example, a policy that restricts the creation of resources without specific tags:

```
   # Ensure resources have required tags
   main = rule {
     all attribute_names as $name {
       $name == "tags" or
       all attribute_values[$name] as $value {
         length($value) > 0
       }
     }
   }
  ```

2. **Policy Testing:**

Use the Sentinel CLI to test your policy locally before applying it to Terraform. This allows you to catch errors and ensure the policy behaves as expected.

```bash
sentinel apply -test
```

3. **Policy Implementation:**
   
Integrate the policy into your Terraform workflow by associating it with a policy set. Configure the enforcement level based on your requirements.

```hcl
terraform {
  sentinel {
    enforce = true
  }
}
```

4. **Policy Management:**
   
Manage policies through the Sentinel CLI or Sentinel Cloud, depending on your preferred workflow.
