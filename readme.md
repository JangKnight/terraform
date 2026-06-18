# SETUP

## Cloud Access (AWS)

1. Create an AWS account if you don't have one already.
2. Use IAM to create CLI role and generate AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY
3. Store ID and KEY in .env file
4. Install AWS CLI and configure with `aws configure`
5. Test with `aws sts get-caller-identity`
6. Install Terraform CLI and use `terraform source .env` to load env vars


## Notes

### Terraform Block

- terraform
- > constants only, no vars or resources allowed. Defines Terraform settings like required providers and version constraints:
```
=  : allows the version specified only
!= : disallows the version specified
>  : allows versions greater than the specified version
>= : allows versions greater than or equal to the specified version
<  : allows versions less than the specified version
<= : allows versions less than or equal to the specified version
~> : allows  versions where the rightmost digit may increment, but not the leftmost (e.g. `~> 2.1` allows `2.1`, `2.1.5`, `2.2`, but not `3.0`)
```

- backend
- - specifies remote state storage (e.g. Terraform Cloud, S3, etc.)
- required_version
- - sets the minimum required Terraform version for the configuration.
- required_providers
- - specifies cloud provider and version constraints
- cloud
- - ...
