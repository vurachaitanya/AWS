Amazon Virtual Private Cloud - (VPC)

- Amazon Virtual Private Cloud (Amazon VPC) enables you to launch AWS resources into a virtual network that you've defined. This virtual network closely resembles a traditional network that you'd operate in your own data center, with the benefits of using the scalable infrastructure of AWS
   - **Virtual private cloud (VPC)** — A virtual network dedicated to your AWS account.
   - **Subnet** — A range of IP addresses in your VPC.
   - **Route table** — A set of rules, called routes, that are used to determine where network traffic is directed. Each route in a route table specifies the range of IP addresses where you want the traffic to go (the destination) and the gateway, network interface, or connection through which to send the traffic (the target)
   - **Internet gateway** — A gateway that you attach to your VPC to enable communication between resources in your VPC and the internet.
   - **VPC endpoint** — Enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the Amazon network.
   - **CIDR block** —Classless Inter-Domain Routing. An internet protocol address allocation and route aggregation methodology. 

- No cost for VPC.
- Max 5 VPC per region  & 200 Subnet per VPC & IPV4 5 CIDR blocks per VPC.
- **public subnet** Use a public subnet for resources that must be connected to the internet.
- **private subnet**  for resources that won't be connected to the internet.
- ** Default VPC ** default VPC that has a default subnet in each Availability Zone.
- ##### By default, each instance that you launch into a nondefault subnet has a private IPv4 address, but no public IPv4 address, unless you specifically assign one at launch, or you modify the subnet's public IP address attribute. These instances can communicate with each other, but can't access the internet.

- **VPC peering** You can create a VPC peering connection between two VPCs that enables you to route traffic between them privately. Instances in either VPC can communicate with each other as if they are within the same network.

- **Transit Gateway** You can also create a transit gateway and use it to interconnect your VPCs and on-premises networks. The transit gateway acts as a Regional virtual router for traffic flowing between its attachments, which can include VPCs, VPN connections, AWS Direct Connect gateways, and transit gateway peering connections.

- **AWS private global network** AWS provides a high-performance, and low-latency private global network that delivers a secure cloud computing environment to support your networking needs. AWS Regions are connected to multiple Internet Service Providers (ISPs) as well as to a private global network backbone, which provides improved network performance for cross-Region traffic sent by customers.
