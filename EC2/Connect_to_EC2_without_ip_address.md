# Connect to EC2 instance without public ip address

* Go to `VPC` -> `Endpoint` -> `Create Endpoint`

    * Assign your endpoint a name
    * Select `EC2 Instance Connect Endpoint` from `Service category`. (Since the goal is to provide access to `EC2 instances without using public IP addresses`, we are choosing the EC2 Instance Connect Endpoint option.)
    * Select the `VPC` where your EC2 instance is reside.