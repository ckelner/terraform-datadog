# Terraform Datadog
Monitoring as Code w/ Terraform &amp; Datadog example

# Noteworthy
- This repo does not use [Terraform
workspaces](https://www.terraform.io/docs/state/workspaces.html); it is a best
practice to use workspaces, this repo is only for example purposes.
- This repo does not use [Terraform remote
state](https://www.terraform.io/docs/state/remote.html); it is a best
practice to use remote state, this repo is only for example purposes.

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

* provider.aws: version = "~> 1.8"
* provider.datadog: version = "~> 1.0"

Terraform has been successfully initialized!

...
```
