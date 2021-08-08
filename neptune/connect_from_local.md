### Connect to AWS Neptune from local system

There are many ways to connect to `Amazon Neptune` from outside of the `VPC`, such as setting up a `load balancer` or `VPC peering`.

Amazon Neptune DB clusters can only be created in an Amazon `Virtual Private Cloud (VPC)`. One way to connect to Amazon Neptune from outside of the VPC is to set up an Amazon EC2 instance as a `proxy server` within the same VPC. With this approach, you will also want to set up an `SSH tunnel to securely forward traffic to the VPC`.

#### Part 1: Set up a EC2 proxy server.

Launch an `Amazon EC2 instance` located in the `same region` as your `Neptune cluster`. In terms of configuration, `Ubuntu` can be used. Since this is a proxy server, you can choose the lowest resource settings.

Make sure the EC2 instance is in the same VPC group as your Neptune cluster. To find the VPC group for your Neptune cluster, check the console under `Neptune > Subnet groups`. The instance's security group needs to be able to send and receive on port `22` for `SSH` and port `8182` for `Neptune`. See below for an example security group setup.

![sample-ec2rules.png](sample-ec2rules.png)

Lastly, make sure you save the key-pair file (.pem) and note the directory for use in the next step.

#### Part 2: Set up an SSH tunnel.

This step can vary depending on if you are running Windows or MacOS.

1. Modify your hosts file to map localhost to your Neptune endpoint.

    Windows: Open the hosts file as an Administrator `(C:\Windows\System32\drivers\etc\hosts)`

    MacOS: Open Terminal and type in the command: `sudo nano /etc/hosts`

    Add the following line to the hosts file, replacing the text with your Neptune endpoint address.

    `127.0.0.1 localhost YourNeptuneEndpoint`

    Open Command Prompt as an Administrator for Windows or Terminal for MacOS and run the following command. For Windows, you may need to run SSH from `C:\Users\YourUsername\`

    `ssh -i path/to/keypairfilename.pem ec2-user@yourec2instanceendpoint -N -L 8182:YourNeptuneEndpoint:8182`

    The `-N` flag is set to prevent an interactive bash session with EC2 and to forward ports only. An initial successful connection will ask you if you want to continue connecting? Type yes and enter.

    To test the success of your local graph-notebook connection to Amazon Neptune, open a browser and navigate to:

    https://YourNeptuneEndpoint:8182/status

    You should see a report, similar to the one below, indicating the status and details of your specific cluster:

		{
		  "status": "healthy",
		  "startTime": "Wed Nov 04 23:24:44 UTC 2020",
		  "dbEngineVersion": "1.0.3.0.R1",
		  "role": "writer",
		  "gremlin": {
		    "version": "tinkerpop-3.4.3"
		  },
		  "sparql": {
		    "version": "sparql-1.1"
		  },
		  "labMode": {
		    "ObjectIndex": "disabled",
		    "DFEQueryEngine": "disabled",
		    "ReadWriteConflictDetection": "enabled"
		  }
		}

#### Close Connection

 	When you're ready to close the connection, use Ctrl+D to exit.
