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
- Set `TF_VAR_datadog_api_key` in your environment. e.g. `export
TF_VAR_datadog_api_key="<your-api-key>"` (note the quotes `""` around the value)

## Init
Run `terraform init` - this will pull down all modules and setup your
local environment to get started with terraform. Output will look similar to the
example below (truncated in places):
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

# Plan
Run `terraform plan -out=plan.out` - this will provide you with a plan of what
terraform will change (commonly known as a "dry run"). The `-out` flag allows us
to save this plan to a file and use it when making the actual changes later. In
this way we can ensure that any local or remote changes that have occurred
between the time we ran `plan` and `apply` are not accepted.

An example of plan output (truncated in places):
```
Refreshing Terraform state in-memory prior to plan...
The refreshed state will be used to calculate this plan, but will not be
persisted to local or remote state storage.

aws_vpc.this: Refreshing state... (ID: vpc-f215b19a)
data.aws_availability_zones.available: Refreshing state...
aws_eip.nat[2]: Refreshing state... (ID: eipalloc-7b1a3055)
...
aws_route.private_nat_gateway[2]: Refreshing state... (ID: r-rtb-e949df811080289494)

------------------------------------------------------------------------

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  + aws_instance.web
      id:                           <computed>
      ami:                          "ami-15e9c770"
      ...

  + aws_key_pair.aws_ssh_key
      id:                           <computed>
      fingerprint:                  <computed>
      key_name:                     "datadog-demo-default"
      ...

  + aws_security_group.web_sg
      id:                           <computed>
      description:                  "Security Group for web node SSH"
      ...
      vpc_id:                       "vpc-f215b19a"

  ...
  + module.http_security_group.aws_security_group_rule.outbound_internet_to_anywhere
      id:                           <computed>
      cidr_blocks.#:                "1"
      cidr_blocks.0:                "0.0.0.0/0"
      from_port:                    "0"
      protocol:                     "-1"
      security_group_id:            "${aws_security_group.sg.id}"
      self:                         "false"
      source_security_group_id:     <computed>
      to_port:                      "0"
      type:                         "egress"


Plan: 9 to add, 0 to change, 0 to destroy.

------------------------------------------------------------------------

This plan was saved to: plan.out

To perform exactly these actions, run the following command to apply:
    terraform apply "plan.out"
```
