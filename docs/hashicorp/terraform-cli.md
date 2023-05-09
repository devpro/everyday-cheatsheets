# Terraform CLI (Command Line Interface)

→ [docs](https://www.terraform.io/docs/cli/index.html)

## Setup

### First installation

* Follow the procedure given in the [Downloads](https://www.terraform.io/downloads.html) page (will depend on the operating system)

### Upgrade

* Read the information given in the [Upgrade Guides](https://www.terraform.io/upgrade-guides/index.html) page (will depend on the version numbers)

## Getting started

* [Use the Command Line Interface by HashiCorp](https://learn.hashicorp.com/collections/terraform/cli)

## commands

### Generic commands

Command                      | Action
-----------------------------|--------------------------------------------------------
`terraform --version`        | Prints the Terraform version
`terraform [command] --help` | Prints help message (general or specific to a command)
`terraform apply`            | Builds or changes infrastructure
`terraform destroy`          | Destroys Terraform-managed infrastructure
`terraform fmt`              | Formats Terraform code
`terraform init`             | Initializes a Terraform working directory
`terraform plan`             | Generates and shows an execution plan
`terraform show`             | Displays human-readable output from a state or plan file
`terraform state`            | Uses state to display resources
`terraform validate`         | Validates the Terraform files

## Examples

```bash
# displays the list of resources managed in the workspace
terraform state list
```
