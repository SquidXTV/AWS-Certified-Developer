## [Amazon Virtual Private Cloud (VPC)](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)
A Virtual Private Cloud (VPC) is a logically isolated virtual network that spans all of the Availability Zones in a Region.

### [VPC Subnets](https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html)
A Subnet partitions the network inside a VPC that is part of a specific Availability Zone.

### [VPC Route Tables](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html)
A route table serves as the traffic controller for your virtual private cloud (VPC).
Each route table contains a set of rules, called routes, that determine where network traffic from your Subnet or Gateway is directed. 

### [VPC Internet Gateway](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html)
An internet gateway enables resources in your Subnet to connect to the internet if the resource has a public IPv4 address or
an IPv6 address. Similarly, resources on the internet can initiate a connection to resources in your Subnet using the public
IPv4 address or IPv6 address.

### [VPC NAT Gateway](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat.html)
A NAT gateway is a Network Address Translation (NAT) service. You can use a NAT gateway so that instances in a private Subnet
can connect to services outside your VPC but external services can't initiate a connection with those instances.

### [VPC Network Access Control Lists](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)
A Network Access Control List (ACL) allows or denies specific inbound or outbound traffic identified by the IP Address and Port
at the Subnet level. These rules are stateless, which means that allowing specific inbound traffic to a Subnet does not
automatically allow outbound traffic for that traffic.

### [Security Groups](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html)
A Security Group controls the traffic that is allowed to reach and leave the resources that it is associated with.
Security Groups are stateful, so that if you send a request from an instance, the response traffic for that request
is automatically allowed to reach the instance regardless of the inbound security group rules.

### [VPC Flow Logs](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html)
VPC Flow Logs is a feature that enables you to capture information about the IP traffic going to and from network interfaces in your VPC.
Flow Logs can be enabled for a VPC, a Subnet, or a Elastic Network Interface. Flow log data for a monitored network interface is recorded
as flow log records, which are log events consisting of fields that describe the traffic flow.

### [VPC Peering Connection](https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html)
A VPC Peering Connection is a networking connection between two VPCs that enables you to route traffic between them using private IPv4 addresses
or IPv6 addresses. Instances in either VPC can communicate with each other as if they are within the same network. VPC Peering Connection is not
transitive, so that only directly peered VPCs can communicate with each other.

### [AWS PrivateLink](https://docs.aws.amazon.com/vpc/latest/userguide/endpoint-services-overview.html)
AWS PrivateLink establishes private connectivity between virtual private clouds (VPC) and supported AWS services, services hosted by other AWS accounts,
supported AWS Marketplace services, and supported resources without going through the public internet. To use AWS PrivateLink, create a VPC endpoint
in any Subnet from which you need to access the service or resource. This creates elastic network interfaces in the specified Subnets that serve as
entry points for traffic destined to the service or resource.

### [AWS Site-to-Site VPN](https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html)
AWS Site-to-Site VPN creates a secure, encrypted IPsec tunnel connection between an on-premises network and a VPC over the public internet.

### [AWS Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html)
Direct Connect links your internal network to an Direct Connect location over a standard Ethernet fiber-optic cable. One end of the cable is
connected to your router, the other to an Direct Connect router. With this connection, you can create virtual interfaces directly to public
AWS services or to Amazon VPC, bypassing internet service providers in your network path.