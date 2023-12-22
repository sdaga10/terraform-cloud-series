# 6.4. Resource Dependencies and Order of Execution

In Terraform, defining dependencies between resources and understanding the order of execution is crucial for ensuring a smooth and predictable infrastructure deployment. This chapter explores how Terraform manages resource dependencies.

## 6.4.1. Defining Resource Dependencies

Resource dependencies are declared using the `depends_on` attribute within a resource block. This ensures that one resource is created or updated before another.

```hcl
resource "aws_instance" "web_server" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}

resource "aws_security_group" "web_sg" {
  name        = "web_sg"
  description = "Security group for web server"
  
  # Dependency on aws_instance
  depends_on = [aws_instance.web_server]
}
```

## 6.4.2. Order of Execution

Terraform determines the order of execution based on dependencies. Resources without dependencies or with resolved dependencies are created or updated first.

## 6.4.3. Parallel Execution

Terraform parallelizes the execution of independent resources when possible, optimizing the deployment speed. Resources with dependencies are still executed in the correct order.

## 6.4.4. Explicit Dependencies

Explicitly defining dependencies ensures that Terraform understands the relationships between resources. This is especially important when dealing with complex infrastructure configurations.

## 6.4.5. Terraform Graph

Use the terraform graph command to visualize the resource dependency graph. This helps in understanding the order in which resources will be created or modified.

```bash
terraform graph | dot -Tpng > graph.png
```

Understanding how Terraform manages resource dependencies and the order of execution is fundamental for designing robust and efficient infrastructure configurations.
