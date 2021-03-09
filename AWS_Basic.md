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


## VPC :
-	VPC is private logical isolated section of AWS Cloud.
-	VPC created private constructs so that applications will be isolated.
-	We can have max of 5 VPC’s in the same region. 
-	We can work with AWS vendor to increase the no of VPC’s per region.
-	By default, VPC created to ease of users by starting.
-	VPC’s can’t span across the regions.
-	By default, we will have 1 VPC and multiple number of AZ and respective subnets (3AZ = 3subnetes)
-	Create VPC and construct based on the requirement. 
-	While creating VPC need to give VPC name, CIDR Block & Tenancy (Dedicated vs default). 
-	If tenancy is dedicated (Not all resources have dedicated mode which might cost you more) EC2 enforced to create the EC2 in dedicated servers locations which would be separated from other customers / accounts. 
-	CIDR , Tenancy can’t be changed after VPC is created. If required recreate a new VPC with new values.
-	All regions have default VPC created by AWS.
-	CIDR : IPv4 has 2^32 Ips
-	2^(32-slashsubnetting) = 2^ (32-24)=2^8=256.
-	5 IP’s reserved for AWS in each subnet. So we can have 251 IP’s available to use. 
-	VPC creation 1. CIDR 2. Choose Tenancy 3. Optional IPV6 CIDR Range.
-	If VPC runs with IPv4 & IPv6 then security, subnet, routing all should be having 2 different stacks for IPv4 & 6 respectively. 

IPv4 | IPv6
---|---
Request for all VPC | Optional
Choise of CIDR Block (/16,/24)| Has fixed sizes of /56 CIDR Block
Choise of CIDR Block| AWS assigns private CIDR, can't select
public and private different| No difference to public vs private, need to have routes & security Policies to make difference

## Subnets :
-	Separates a specified CIDR range within an AZ
-	A segment of a VPC that lives entirely within a single AZ.
-	Subnet can’t span more than one AZ
-	Subnet can be public, private or VPN only

#### Private Addressing spaces
Start IP|End IP|Offers|Range
---|---|---|---|
192.168.0.0|192.168.255.255|1|16
172.16.0.0|172.31.255.255|16|16
10.0.0.0|10.255.255.255|256|16
