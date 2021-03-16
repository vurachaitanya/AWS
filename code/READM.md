## POC on AWS 
#### [Reff link of the code](https://nickcharlton.net/posts/terraform-aws-vpc.html)

#### USE Case :
-	Create VPC with 2 Subnet (Public, Private)
-	Create 2 EC2 instances in each subnet with having access to public and private
-	Only Public EC2 instance should have external access and Private EC2 should not.
-	Routes should be connected across two EC2 for communicating each other. 
-	User ingress/egress or SG for traffic routing.
