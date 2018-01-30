# Terraform Datadog
Monitoring as Code w/ Terraform &amp; Datadog example

# Use
## Init
```
⇒  aws-vault exec demo-account-admin terraform init
Initializing modules...
- module.vpc
  Found version 1.17.0 of terraform-aws-modules/vpc/aws on registry.terraform.io
  Getting source "terraform-aws-modules/vpc/aws"

Initializing provider plugins...
- Checking for available provider plugins on https://releases.hashicorp.com...
- Downloading plugin for provider "datadog" (1.0.3)...
- Downloading plugin for provider "aws" (1.8.0)...

The following providers do not have any version constraints in configuration,
so the latest version was installed.

To prevent automatic upgrades to new major versions that may contain breaking
changes, it is recommended to add version = "..." constraints to the
corresponding provider blocks in configuration, with the constraint strings
suggested below.

* provider.aws: version = "~> 1.8"
* provider.datadog: version = "~> 1.0"

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```
