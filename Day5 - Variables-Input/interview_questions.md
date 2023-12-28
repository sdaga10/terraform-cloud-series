# Interview Questions: Terraform Variables and Inputs

1. **What is the purpose of input variables in Terraform?**
   - *Answer:* Input variables allow dynamic values to be provided when running Terraform, making configurations more flexible and reusable.

2. **How do you declare an input variable in Terraform?**
   - *Answer:* Input variables are declared using the `variable` block in the configuration, specifying the variable name and type.

3. **Explain the difference between required and optional variables.**
   - *Answer:* Required variables must be provided with values during Terraform execution, while optional variables have default values but can be overridden if needed.

4. **How can you pass values to input variables during Terraform execution?**
   - *Answer:* Values for input variables can be provided using command-line flags, variable files, or environment variables.

5. **What is a variable file, and how is it used in Terraform?**
   - *Answer:* A variable file is a separate file containing variable values. It is used to organize and reuse variable values across multiple Terraform runs.

6. **Explain the use of environment variables in Terraform for variable values.**
   - *Answer:* Environment variables can be prefixed with `TF_VAR_` to set values for corresponding Terraform variables, providing a way to keep sensitive information secure.

7. **How do you handle sensitive information, such as API keys, in Terraform variables?**
   - *Answer:* Sensitive information can be handled using sensitive variable types or by leveraging environment variables and external tools for secret management.

8. **Can you use expressions or functions in variable values? Provide an example.**
   - *Answer:* Yes, expressions and functions can be used in variable values. Example: `${var.environment == "production" ? "high" : "low"}`.

9. **What is variable interpolation in Terraform?**
   - *Answer:* Variable interpolation is the process of referencing the values of variables within strings or expressions using the `${}` syntax.

10. **How can you validate variable values in Terraform?**
    - *Answer:* Variable validation rules can be defined using the `validation` block within the `variable` block, ensuring that values meet specific criteria.

11. **Explain the concept of variable defaults and when you would use them.**
    - *Answer:* Variable defaults provide fallback values if no value is provided during execution. They are useful for making variables optional or providing default behavior.

12. **In what scenarios would you use locals instead of variables?**
    - *Answer:* Locals are used for expressions or values that are computed once and reused within the configuration, providing a cleaner way to organize complex expressions.
