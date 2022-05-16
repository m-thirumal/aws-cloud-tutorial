# Chalice multi-stage deployment
1. Add stages config on `.chalice/config.json` file.  
2. Example: `dev` and `prod` stages
```
  {
    "version": "2.0",
    "app_name": "test-stage",
    "stages": {
      "dev": {
        "autogen_policy": false,
        "iam_policy_file": "policy.json",
        "api_gateway_stage": "api",
        "environment_variables": {
          "env1": "dev-values"
        },
        "subnet_ids": ["subnet-dev"],
        "security_group_ids": ["sg-dev"]
      },
      "prod": {
        "autogen_policy": false,
        "iam_policy_file": "policy.json",
        "api_gateway_stage": "api",
        "environment_variables": {
          "env1": "pro-values"
        },
        "subnet_ids": ["subnet-prod"],
        "security_group_ids": ["sg-prod"]
      }
    }
  }
``` 
3. To deploy, run the following commands
      
       chalice deploy --stage prod
       chalice deploy --stage dev
