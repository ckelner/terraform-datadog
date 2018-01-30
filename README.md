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
## Setup
- Define AWS authentication via Environment, Shared Creds file, etc as
documented in the [Terraform AWS Provider
docs](https://www.terraform.io/docs/providers/aws/index.html#environment-variables)
- Define `DATADOG_API_KEY` and `DATADOG_APP_KEY` in environment variables per
the [Terraform
documentation](https://www.terraform.io/docs/providers/datadog/index.html)
- Set `TF_VAR_DATADOG_API_KEY` in your environment. e.g. `export
TF_VAR_DATADOG_API_KEY=<your-api-key>`

## Init
Run `terraform init` - this will pull down all modules and setup your
local environment to get started with terraform. Output will look similar to the
example below:
```
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
