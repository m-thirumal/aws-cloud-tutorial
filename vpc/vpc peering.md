# VPC Peering b/w accounts

1. Go to VPC service and create `VPC and More` 

!> Make sure both VPC are in different CIDR range

2. Then, go to VPC -> `Peering Connection` and enter the another account ID and VPC ID.

3. Accept the request from the another account

4. Go to the `Route Table` and add new route to the another account `CIDR range`. Do the same on both account

5. Check the connection