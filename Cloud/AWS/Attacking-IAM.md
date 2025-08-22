# Attacking IAM in AWS

### Cheatsheet for IAM enumeration

#### Setup
- Configure Profile = `$ aws configure --profile <CLOUD>`
- Paste your Access Key ID and Secret access key
- Whoami = `$ aws sts get-caller-identity --profile <CLOUD>`
- User info = `$ aws iam get-user --profile <CLOUD>`

#### Users
- List IAM users = `$ aws iam list-users`
- List Access keys [This can be abused if they only have 1] = `$ aws iam list-access-keys --profile <CLOUD>`

#### User Permissions
- List attached managed policies = `$ aws iam list-attached-user-policies --user-name <USERNAME> --profile <CLOUD>`
- List inline policies = `$ aws iam --user-policies --user-name <USERNAME> --profile <CLOUD>`
- Get inline policy details = `$ aws iam get-user-policy --user-name <USERNAME> --policy-name <POLICYNAME> --profile <CLOUD>`

#### Groups and Permissions
- List groups for a user = `$ aws iam list-groups-for-user --user-name <USERNAME> --profile <CLOUD>`
- List group policies = `$ aws iam list-group-policies --group-name <GROUP> --profile <CLOUD>` OR `$ aws iam list-attached-group-policies --group-name <GROUP> --profile <CLOUD>`
- Get inline group policy details = `$ aws iam get-group-policy --group-name <GROUP> --policy-name <POLICY>`

#### Roles and Permissions
- List all roles = `$ aws iam list-roles`
- Get role details = `$ aws iam get-role --role-name <ROLE_NAME>`
- List attached policies = `$ aws iam list-attached-role-policies --role-name <ROLE_NAME>`
- List Inline policies = `$ aws iam list-role-policies --role-name <ROLE_NAME>`
- Get inline role policy details = `$ aws iam get-role-policy --role-name <ROLE_NAME> --policy-name <POLICY_NAME>`

#### Get Policy Documents
- Get managed policy doc by name = `$ aws iam get-policy --policy-arn <POLICY_ARN>`
- Get managed policy doc by ARN = `$ aws iam get-policy-version --policy-arn <POLICY_ARN> --version-id <VERSION_ID>`

#### View IAM snapshot
- Dump all permissions = `$ aws iam get-account-authorization-details`
