
# Chapter 11.4: Functions and Expressions

In Terraform, functions and expressions play a crucial role in manipulating data and generating dynamic configurations. Functions allow you to perform various operations, such as string manipulation, mathematical calculations, and data formatting, within your Terraform configurations.

## Using Functions

Terraform provides a wide range of built-in functions that you can leverage to manipulate data and perform complex operations. Some common functions include:
- `concat`: Concatenates multiple strings together.
- `element`: Retrieves an element from a list or map.
- `join`: Joins elements of a list into a single string with a separator.
- `format`: Formats a string according to a specified format specifier.
- `lookup`: Looks up a value in a map given a key.

## Expressions

Expressions in Terraform allow you to dynamically compute values based on variables, functions, and other expressions. You can use expressions to create conditional logic, perform arithmetic operations, and generate dynamic resource configurations based on input data.

### Example:

```hcl
variable "environment" {
  type    = string
  default = "dev"
}

resource "aws_instance" "example" {
  count         = var.environment == "dev" ? 1 : 0
  instance_type = var.environment == "dev" ? "t2.micro" : "t2.large"
  ami           = var.environment == "dev" ? "ami-12345678" : "ami-87654321"
}
