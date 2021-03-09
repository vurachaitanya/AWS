## AWS Basics

-	Routers table for two regions and VPC peering connection would be created for communicating two regions. 
-	Regions are geographically separated locations
-	Availability zones are having different datacenters in same region.
-	Resources are isolated across the regions 
-	VPC Internet gateway, routing tables, VPC pools are used to connect resources between 2 regions.
-	Availability zones can be from 2 to 5 and are naming convention given as us-west-2a, us-west-2b, us-west-2c, us-west-2d  
-	Subnet allocation will show different AZ and default Subnet.
-	Only few resources are span across AZ like EC2, LB, etc.
-	AZ naming convention differs from one account to another as if all uses us-west-2a will have load on only one datacenter. Hence it differs from one account to another.
-	Edge location are different from AZ, it can be a 1 RAC location or multiple server rac solution available to customers to provide low latency content deliver.
-	Edge locations caches the data from customers and servers from next time.
-	Edge locations are been rapidly increasing to server the cache for datacenters/AZ/Regions.
-	Infrastructure.aws will show the AWS edge locations. Regions and speeds etc.
-	VPC span across the AZ
-	AZ’s are logically separated, and resources can be pulled from different datacenters of same region.
-	Subnets are bound to AZ.
![](https://github.com/vurachaitanya/AWS-CLI/blob/master/images/Public_vs_Private.JPG)
-	Public net – access to out side of the world
-	Private net – access to inter AZ location resources. 
-	VPC give access of objects inside the region to outside world.
-	Few services are only region specific like S3, CloudWatch, Cloudformation, DynamoDB, Workspace,
-	Few servers are only AZ specific, Subnet, EC2, etc.
-	Few services are out size of region or across the accounts like Route 53, cloud front edge locations, AWS Direct connect location.
-	Internal to VPC are call private services and out side of VPC are call public services.
