# Multiple Region Implementation in Terraform

You can make use of `alias` keyword to implement multi region infrastructure setup in
terraform.

```
provider "aws" {
  alias = "us_east_1"   # the alias can be any name you choose.
  region = "us-east-1"
}

provider "aws" {
  alias = "us_west_2"
  region = "us-west-2"
}

resource "aws_instance" "example" {
  ami = "ami-0123456789abcdef0"
  instance_type = "t2.micro"
  provider = "aws.us_east_1"   # Here you are making reference to the alias of your choosen region.
}

resource "aws_instance" "example2" {
  ami = "ami-0123456789abcdef0"
  instance_type = "t2.micro"
  provider = "aws.us_west_2"
}
```
