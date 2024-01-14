# 9.1. Provisioners and Their Use Cases

## Introduction

Provisioners in Terraform are used to execute scripts or tasks on a local or remote machine as part of resource creation or destruction. They provide a way to perform actions such as software installation, configuration management, or any other tasks required to set up or clean up resources. While provisioning can be a powerful tool, it's essential to use them judiciously and understand their implications.

## Types of Provisioners

Terraform supports various types of provisioners:

1. **Local-exec Provisioner:** Executes commands on the machine running Terraform. Useful for tasks that need to be performed locally.

2. **Remote-exec Provisioner:** Connects to a resource using SSH or WinRM and executes commands. Commonly used for remote configuration tasks.

3. **File Provisioner:** Copies files or directories from the machine running Terraform to the newly created resource.

## Use Cases for Provisioners

### 1. Software Configuration

Provisioners are often used to install and configure software on a newly created resource. For example, installing specific packages, setting up configurations, or initializing databases.

```hcl
resource "aws_instance" "example_instance" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  provisioner "remote-exec" {
    inline = [
      "sudo apt-get update",
      "sudo apt-get install -y nginx",
    ]
  }
}
```

### 2. Initialization Scripts

Provisioners can execute initialization scripts to prepare a resource for its intended use. This is common when setting up servers or virtual machines with specific roles.

```hcl
resource "aws_instance" "example_instance" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  provisioner "local-exec" {
    command = "./init_script.sh"
  }
}
```

### 3. Configuration Management

For resources that require complex configuration management, provisioners can be used to apply configurations using tools like Ansible, Chef, or Puppet.

```hcl
resource "aws_instance" "example_instance" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  provisioner "remote-exec" {
    script = "configure_instance.sh"
  }
}
```

### 4. Post-Destruction Cleanup

Provisioners can also be used in the destroy phase to perform cleanup tasks after a resource is destroyed.

```hcl
resource "aws_instance" "example_instance" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  provisioner "local-exec" {
    when    = "destroy"
    command = "echo 'Resource destroyed.'"
  }
}
```


