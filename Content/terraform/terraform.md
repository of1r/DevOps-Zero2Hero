# The following readme will explain about terraform, use cases and commands.
## What is it terraform?
 terraform its an IAC - infrastructure as a code that gives the opportunity to manage your infra using a simple code
 terraform supports multiple providers for example: AWS,GCP,Azure,VMware and more
### Adventages
- Gives the abillity to work as a team (lock the state when applying changes)
- Supports a varity of cloud providers
- Clear offical documantation for most use cases and examples
- Create/Destroy resources in one click
- Supports scripts that span many regions - for example ec2 instance we can use in each region his own AMI

### Disadventages
- Terraform saves the configuration on state file if the file is corrupted it can lead to resource managment issues
- Terraform may not support some resources of their latest features
- No error handling so you need to debug by yourself the issues
- While Terraform does provide ways to manage dependencies between resources, complex dependencies across multiple modules or       environments can become difficult to manage

### Basic therms on terraform
