# 2.1. Installing Terraform

Terraform is a powerful Infrastructure as Code (IaC) tool that allows you to define and provision infrastructure in a declarative configuration language. Before you can start using Terraform, you need to install it on your machine.

## Prerequisites

Before installing Terraform, ensure that you have the following prerequisites:

- [ ] **Operating System:** Terraform supports various operating systems, including Windows, macOS, and Linux. Choose the appropriate installation method for your OS.

- [ ] **Internet Connection:** The installation process may require an internet connection to download the Terraform binary.

## Installation Steps

Follow these steps to install Terraform on your machine:

### For Windows:

1. **Download Terraform:**
   Visit the [official Terraform website](https://www.terraform.io/downloads.html) and download the Windows version of Terraform.

2. **Extract the Zip File:**
   Extract the downloaded Zip file to a location of your choice.

3. **Add to System PATH:**
   Add the path to the Terraform executable to your system's PATH environment variable. This step is crucial for running Terraform commands from any location in the command prompt.

4. **Verify Installation:**
   Open a new command prompt and run the following command to verify that Terraform is installed:

   ```bash
   terraform --version
