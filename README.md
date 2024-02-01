# Tailcall on AWS
This repo lets you deploy a Tailcall instance with your own config on AWS (Lambda and API Gateway). The deployment is automatically built and managed by Terraform, but you can customize it by editing `tailcall.tf`.

## First setup
1. [Install Terraform.](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)
1. Create an access key on AWS, and set your `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variables.
1. Fork this repo and clone it.
1. Run `terraform init` and `terraform apply`.
1. Done! The API Gateway URL of your Tailcall deployment should be logged to the console. 🎉

## Changing your deployment
If you change `config.graphql`, you can update your deployment with the new config by running `terraform apply` again. This will also auto-update Tailcall if a new version has been released since the last time you've applied the Terraform config.s

## Teardown
If you want to delete your deployment, run `terraform destroy`. This will delete your Lambda function and API Gateway from AWS.
