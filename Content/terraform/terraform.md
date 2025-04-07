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

### Basic therms in terraform
- The extention of the file should be .tf for terraform usage  naming isnt mandatory but recommended to work with the following way: 
- modules - Create multiple resources using modules you can use the offical modules that created by the providers and you also can create your own module (if you want to create specific resources and not what created with the official module) 
example using of using a module, this will create a bucket in s3 on aws with the name test-bucket
```
module "s3-bucket" {
  bucket = "test-bucket"
  source  = "terraform-aws-modules/s3-bucket/aws"
  version = "4.6.0"
}
```
- variables - Gives the abillity to configure them in one place and not repeat clear text definitions on your code you just need to call the variable you want recommended to use in 
