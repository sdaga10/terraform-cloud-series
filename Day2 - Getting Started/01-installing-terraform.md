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

### For macOS:

**Install with Homebrew:**

Open a terminal and run the following Homebrew command to install Terraform:

```bash
brew install terraform

**Verify Installation:**
Open a new command prompt and run the following command to verify that Terraform is installed:

```bash
terraform --version


### For Linux:

**Download Terraform:**

Open a terminal and run the following command to install Terraform:

wget https://releases.hashicorp.com/terraform/<VERSION>/terraform_<VERSION>_linux_amd64.zip
unzip terraform_<VERSION>_linux_amd64.zip
sudo mv terraform /usr/local/bin/

Replace <VERSION> with the desired Terraform version.

**Verify Installation:**
Open a new command prompt and run the following command to verify that Terraform is installed:

```bash
terraform --version


