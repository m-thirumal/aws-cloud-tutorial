1. Create repository in AWS codecommit or github

2. Create a bucket to host website, follow the instructions [S3-Host static website](../S3-Host%20static%20website/host_static_website_using_s3.md)

3. Go to AWS CODEPIPELINE, Create New

	* Source - Select the repository and branch
	* Build  - Create new project with `buildspec.yml` options
		* Create `buildspec.yml` file in the reactjs repository with the following contents

				version: 0.2

				phases:
				  pre_build:
				    commands:
				      - npm install
				  build:
				    commands:
				      - npm run build

				artifacts:
				  files:
				    - '**/*'
				  discard-paths: no
				  base-directory: build
	* Deploy - Select the bucket you want to deploy.
