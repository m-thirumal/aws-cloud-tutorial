### Add/Modify the default policy

1. Create project will automatically create .chalice/config.json file

        {
          "version": "2.0",
          "app_name": "eballot-add-signup-user",
          "stages": {
            "dev": {
               "api_gateway_stage": "api"
            }
          }
        }


2. To add policy for each environment, add the policy json file to the same directory

        {
          "Version": "2012-10-17",
          "Statement": [
            {
              "Action": [
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:PutLogEvents"
              ],
              "Resource": "arn:aws:logs:*:*:*",
              "Effect": "Allow"
            },
            {
              "Sid": "VisualEditor0",
              "Effect": "Allow",
              "Action": "kinesis:*",
              "Resource": "*"
            }
          ]
        }

3. Modify the `config.json` with policy file name and stage

        {
          "version": "2.0",
          "app_name": "eballot-add-signup-user",
          "stages": {
            "dev": {
               "autogen_policy": false,
               "iam_policy_file": "policy-dev.json",
               "api_gateway_stage": "api"
            }
          }
        }


    
