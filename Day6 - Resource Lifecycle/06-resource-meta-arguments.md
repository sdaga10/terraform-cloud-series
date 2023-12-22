# 6.6. Resource Meta-Arguments

In Terraform, resource meta-arguments provide additional configuration options for resources, allowing you to control various aspects of their behavior. This chapter explores common meta-arguments and their use cases.

## 6.6.1. Count and For Each

The `count` and `for_each` meta-arguments enable you to create multiple instances of a resource based on a numeric count or a set of unique values, respectively.

```hcl
resource "aws_instance" "web_servers" {
  count = 3

  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```
```hcl
resource "aws_instance" "web_servers" {
  for_each = {
    server1 = "us-west-1",
    server2 = "us-east-1",
    server3 = "eu-west-1",
  }

  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
  region        = each.value
}
```

## 6.6.2. Depends On

The depends_on meta-argument allows you to explicitly define dependencies between resources. It ensures that a particular resource is created or updated only after the resources specified in depends_on are created.

```hcl

resource "aws_security_group" "web_sg" {
  name        = "web_sg"
  description = "Security group for web server"
}

resource "aws_instance" "web_server" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  depends_on = [aws_security_group.web_sg]
}
```

## 6.6.3. Provisioner Meta-Arguments

Provisioner meta-arguments like connection and provisioner allow you to define how Terraform communicates with the created instances and configure post-creation actions.

```hcl

resource "aws_instance" "web_server" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  connection {
    type        = "ssh"
    user        = "ubuntu"
    private_key = file("~/.ssh/id_rsa")
  }

  provisioner "remote-exec" {
    inline = [
      "sudo apt-get update",
      "sudo apt-get install -y nginx",
    ]
  }
}
```

Understanding and leveraging resource meta-arguments enhances the flexibility and control you have over your infrastructure configuration.
