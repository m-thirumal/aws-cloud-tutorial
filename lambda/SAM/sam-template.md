# SAM Template


#### Add Environment variables

	Resources:
	  HelloWorldFunction:
	    Type: AWS::Serverless::Function # More info about Function Resource: https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md#awsserverlessfunction
	    Properties:
	      CodeUri: eballot_presignup/
	      Handler: app.lambda_handler
	      Runtime: python3.8
	      Environment:
	        Variables:
	          APP_TABLE_NAME: user


### Permission/Policy for lambda Function


	Resources:
	  HelloWorldFunction:
	    Type: AWS::Serverless::Function # More info about Function Resource: https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md#awsserverlessfunction
	    Properties:
	      CodeUri: eballot_presignup/
	      Handler: app.lambda_handler
	      Runtime: python3.8
	      Environment:
	        Variables:
	          APP_TABLE_NAME: user
	      Policies:
	        # Give DynamoDB Full Access to your Lambda Function
	        - AmazonDynamoDBFullAccess
