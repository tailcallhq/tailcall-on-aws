# Tailcall on AWS
This repo lets you deploy a Tailcall instance with your own config on AWS (Lambda and API Gateway). The deployment is automatically built and managed by Terraform, and it will use the config in `config/config.graphql`. The whole `config/` directory will be uploaded to AWS, so you can use `@link` with other files in the directory.

## First setup
1. [Install Terraform.](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)
1. Create an access key on AWS, and set your `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variables.
1. Open this repo on GitHub, click on "Use this template" to create a new repository with it, and clone it to your machine.
1. In the repo's directory, run `terraform init` and `terraform apply`.
1. Done! The API Gateway URL of your Tailcall deployment should be logged to the console. 🎉

## Changing your deployment
If you change `config/config.graphql`, you can update your deployment with the new config by running `terraform apply` again. This will also auto-update Tailcall if a new version has been released since the last time you've applied the Terraform config.

## Configuring your deployment
You can configure certain functionality of your deployment by creating the `config/.env` file. The following environment variables are checked:
- `LOG_LEVEL`: Sets minimum log level that will be uploaded to AWS CloudWatch. Available values: `TRACE` (default, will log everything), `DEBUG`, `INFO`, `WARN`, `ERROR`.

## Teardown
If you want to delete your deployment, run `terraform destroy`. This will delete your Lambda function and API Gateway from AWS.
