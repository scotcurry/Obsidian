**Note:** This assumes that the AWS credentials live in the ~/.aws/credentials file

You start with a main.tf file in a folder.  That file provides two key pieces of information: 1) the **provider** and the resource.

Provider tells Terraform what batch of libraries to pull in.  In the case of buildiing a Kubernetes cluster on AWS, you use
```
provider "aws" {
  region = "us-east-1"
}
```
For the example I wanted to build a subnet so I also added
```
resource "aws_vpc" "currywarevcp" {
  cidr_block = "10.0.0.0/16"
}
```
### Run Terraform INIT### (all lower case)
