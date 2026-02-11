---
name: infrastructure-as-code
description: "Define, deploy, and manage infrastructure as code using tools like Terraform or Pulumi. This skill enables the agent to automate the provisioning and management of cloud resources, ensuring consistency, repeatability, and version control of your infrastructure."
license: "MIT"
---

## Workflow

1.  **Define Infrastructure:** The user specifies the desired infrastructure in a high-level configuration language (e.g., HCL for Terraform, or a general-purpose programming language for Pulumi).
2.  **Generate Code:** The agent generates the corresponding infrastructure-as-code (IaC) files.
3.  **Review and Approve:** The user reviews the generated code and approves the changes.
4.  **Apply Changes:** The agent uses the IaC tool to apply the changes and provision the infrastructure on the target cloud provider.
5.  **Manage State:** The agent manages the state of the infrastructure, allowing for future updates and modifications.

## Usage

To use this skill, the user should provide a clear description of the desired infrastructure, including:

*   The cloud provider (e.g., AWS, Azure, GCP).
*   The resources to be created (e.g., virtual machines, databases, networks).
*   The configuration of each resource (e.g., instance size, storage capacity, security rules).

The agent will then generate the necessary IaC code and guide the user through the deployment process.

## Example

**User Request:**

> "Create a new S3 bucket in AWS named 'my-awesome-bucket' for storing public images."

**Agent Action:**

The agent would generate a `main.tf` file for Terraform:

```terraform
resource "aws_s3_bucket" "my_bucket" {
  bucket = "my-awesome-bucket"
  acl    = "public-read"
}
```

Then, the agent would execute the following commands:

1.  `terraform init`
2.  `terraform plan`
3.  `terraform apply`

This would create the S3 bucket with the specified configuration.
