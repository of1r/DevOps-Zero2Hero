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
provider.tf - for provider configuration
main.tf - primary configuration file contains all infrastrcture resources
variables.tf - definition of all variables 
outputs.tf - display values or use them for other configurations
- modules - Create multiple resources using modules you can use the offical modules that created by the providers and you also can create your own module (if you want to create specific resources and not what created with the official module) 
example using of using a module, this will create a bucket in s3 on aws with the name test-bucket
```
module "s3-bucket" {
  bucket = "test-bucket"
  source  = "terraform-aws-modules/s3-bucket/aws"
  version = "4.6.0"
}
```
- variables - Gives the abillity to configure them in one place and not repeat clear text definitions on your code you just need to call the variable you want.
example of variable usage
```
variable "image_id" {
  type        = string
  description = "The id of the machine image (AMI) to use for the server."
}
imageid = var.image_id
```
- outputs - Gives the abillity to display values or use them on other resources
example:
```
output "instance_public_ip" {
  value       = aws_instance.example.public_ip
  description = "The public IP of the EC2 instance"
}
resource "aws_security_group" "example" {
  name        = "example-sg"
  description = "Allow SSH from EC2 instance"

  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["${output.instance_public_ip}/32"]
  }
}
```
- provider - where you need to define all the required information for terraform to connect to your provider(region,access key and secret keys,) where do you want to save the state(s3 - using dynamodb to lock the state)
example:
```
provider "aws" {
  region     = "us-west-2"
  access_key = "my-access-key"
  secret_key = "my-secret-key"
}
```
- resource - mainly as a part of modules can be created seperatly without being a part of any module
- here is an example:
```
resource "azurerm_resource_group" "jacks-rg" {
  name     = "jacks-rg"
  location = "UK South"
}
```
### Important commands
On each folder before applying resources you need to install the plugins the requires for the terraform files so you need to run on the first time(if you change the location of the state file you will need to run init again) the following command:
```
terraform init
```
Before you apply the changes you can view what affects your configuration files will do to the infrastructure, what should be create, destroy, changes etc(to plan the changes)
For that you will use
```
terraform plan
```
When you saw the exceution of the plan results you now can apply the changes(this command do terraform plan and apply together)
you will need to approve that by writing yes/no
```
terraform apply
```
To destroy resources you will need to write the following command and apporve that  with yes/no answer
```
terraform destroy
```
