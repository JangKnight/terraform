# SETUP

## Cloud Access (AWS)

1. Create an AWS account if you don't have one already.
2. Use IAM to create CLI role and generate AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY
3. Store ID and KEY in .env file
4. Install AWS CLI and configure with `aws configure`
5. Test with `aws sts get-caller-identity`
6. Install Terraform CLI and use `terraform source .env` to load env vars
