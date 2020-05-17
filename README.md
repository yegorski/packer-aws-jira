# Jira AWS AMI with Packer

Packer Ansible script for provisioning an Atlassian Jira AWS AMI.

Installs Jira version 7.13.0.

## Prerequisites

1. Install [HashiCorp Packer][].
1. Set AWS account key and secret. Do this in one of two ways:
   1. Use a tool like [aws-vault][].
   1. Export your IAM user's `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`.
1. Run `export AMI_USERS=YOU_AWS_ACCOUNT_ID` to grant your AWS account permission to use the AMI.
1. Post-installation, Jira will need a database. Use a local DB (not recommended for production), install your own, or use the example here [terraform-aws/jira][] to create a Postgres 9.6 RDS instance.

## Usage

```bash
packer build jira.json
```

Use the AMI ID (printed in the output) when you create the Jira AWS EC2 instance.

See [terraform-aws-jira][] Terraform module for how to create the EC2 instance and start using Atlassian Jira.

## Testing

### Ansible

The Ansible is linted using Molecule. Molecule does much more than lint. To learn more, see [Testing Ansible roles with Molecule][].

You can also use the `jira` Ansible inventory to create a local VirtualBox VM to test with Vagrant.

### Packer

Packer file syntax of `sonarqube.json` is tested using Packer's `validate` command.

[aws-vault]: https://github.com/99designs/aws-vault
[hashicorp packer]: https://www.packer.io/
[terraform-aws-jira]: https://github.com/yegorski/terraform-aws-jira
[terraform-aws/jira]: https://github.com/yegorski/terraform-aws/tree/master/terraform-aws-jira
[testing ansible roles with molecule]: https://opensource.com/article/18/12/testing-ansible-roles-molecule
