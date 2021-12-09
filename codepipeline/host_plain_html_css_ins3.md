1. Create a repository in AWS codecommit or Github
2. Add `buildspec.yml` file in root directory 
3. Create a bucket to host website, follow the instructions [S3-Host static website](../S3-Host%20static%20website/host_static_website_using_s3.md)

4. Go to AWS CODEPIPELINE, Create New

	* Source - Select the repository and branch
	* Build  - Create a new project with `buildspec.yml` options
		* Create `buildspec.yml` file in the reactjs repository with the following contents

				version: 0.2
				artifacts:
				  files:
				    - '**/*'
				  discard-paths: no
                  
	* Deploy - Select the bucket you want to deploy.
