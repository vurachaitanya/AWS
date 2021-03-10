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
![VPC to VPC communication](https://github.com/vurachaitanya/AWS/blob/master/images/AWS_Subnets.JPG)
-	Separates a specified CIDR range within an AZ
-	A segment of a VPC that lives entirely within a single AZ.
-	Subnet can’t span more than one AZ
-	Subnet can be public, private or VPN only
-	Make sure you don’t have overlapping ip address range. As AWS will allow to do it.
-	Once VPC is created we can’t change CIDR so make sure those IP’s can’t overlapped across VPC’s.
-	Make sure no overlap across vpc and on-premise networks. 
-	Avoid using the default VPC if your VPC will communicate with other VPC’s.
-	**Default VPC :**  172.31.0.0/16
-	While creating Subnets 1. Specify Target AZ, 2. Determine CIDR Range (Small: /28, to /16) 3. AWS Reserved first 4 IP’s addresses & Last IP add of the subnet for internal networking purposes. 
-	With every VPC we will have one routing entry is created in VPC Route.
-	Each entry has one destination and target.
-	Multiple routes can be added 
-	Targets can be Internet gateways, Cloud gateways,  NAT Gateways.
-	Local target entry is default for each subnet and can’t be removed. 
-	You can create custom route table for each subnet and main would be fall back.
-	In VPC we will have VPC Router in Public network and Internet gateway (IGW) acts as communication channel between public and private networks. Virtual private gateway (VPG) to expose to the outside of the cloud or VPC.
-	If we want to expose S3 in private subnet we need to add VPC routers, internet gateway for which we will add route table with 0.0.0.0/0 target with internet gateway to expose S3 bucket. 
-	[Find next CIDR](https://cidr.xyz/)
-	Create custom VPC with 10.0.0.0/16 subnet.
-	Create routes for 2 applications (Web & Database) in two AZ (us-east1a & us-east1b) = 4 routes.
-	Create 4 routes with 10.0.0.0/21, 10.0.8.0/21, 10.0.64.0/21, 10.0.72.0/21
-	Create 4 route tables with our custom VPC created above. 
-	Associate DB routes with associated subnets routes table. So that it uses specified other than default route table.
-	By default route table has VPC info(10.0.0.0/16). We can add 0.0.0.0/0 if we want to expose route to external world using Internet gateways or other sources. 


#### Private Addressing spaces
Start IP|End IP|Offers|Range
---|---|---|---|
192.168.0.0|192.168.255.255|1|16
172.16.0.0|172.31.255.255|16|16
10.0.0.0|10.255.255.255|256|16

## VPC Router
- AZ vs Subnet vs Routers vs Routing table
![Routers vs Subnet vs AZ vs Routing table](https://github.com/vurachaitanya/AWS/blob/master/images/AWS_Routers.JPG)
-	VPC Router is not created explicitly. With out VPC router VPC can’t route the traffic. 
-	First place packets hit when leaving resources that are in the VPC/Subnet.
-	Routing decisions are governed by route tables associated with VPC.
-	VPC router will not be shows in AWS Console.
-	For each subnet automatically VPC Router is created
-	For communicating two different AZ’s, VPC Router communicates with respective AZ VPC Routers.
-	VPC Router will act as DHCP and provide the ip addresses which includes DNS & Default gateway.
-	Default gateway would be VPC router. 
-	By Default DNS would be served, but can be changed if in case we are working on complex env and to have dedicated DNS.
-	When VPC is created, it creates route table. 
-	VPC Routers are Highly available devices and it occupies the .1 addressing space on every subnet associated with VPC.
-	By default, it allows communications between subnets in the same VPC. This is  what the static “local” route table entry defines.
-	You can influence the routing for your VPC by editing the main route tables or creating custom route tables for each of the subnets.


#### AWS Reserves IP Address:
-	CIDR Range of 10.0.64.0/21 following 5 Ips are reserved
-	10.0.64.0: Network Address
-	10.0.64.1: Reserved by AWS for the VPC Router
-	10.0.64.2: The IP address for the DNS servers.
-	10.0.64.3: reserved by AWS for future use.
-	10.0.71.255: Network broadcast address.
-	By default AWS VPC will not allow broadcast addresses. 
