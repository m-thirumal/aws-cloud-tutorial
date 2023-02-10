## Delete all user from the Cognito user pool

## Dependency

1. `aws cli` & set up `IAM` config in home directory

2. Install [JQ](https://stedolan.github.io/jq/download/)


### Command to delete all users

Replace the variable `COGNITO_USER_POOL_ID`  with `Pool Id` in the following command

```
aws cognito-idp list-users --user-pool-id $COGNITO_USER_POOL_ID | jq -r '.Users | .[] | .Username' | while read uname1; do echo "Deleting $uname1"; aws cognito-idp admin-delete-user --user-pool-id $COGNITO_USER_POOL_ID --username $uname1; done
```
