
# VPC : Course on Udemmy by Stepahane Mareek

## Cloud Research

### VPC 
VPC is Virtual Private Cloud,private network to deploy your resources (regional resource)

Subnets allow you to partition your network inside your VPC (Availability Zone resource).
there are 2 subnets that you should know :
- Public subnet is a subnet that can be accessed from the internet
- Private subnets are subnets that are not accessible from the internet

To define access to the internet and between subnets, we use Route Tables

### Internet Gateway & NAT Gateways
- Internet Gateways helps our VPC instances connect with the internet
- Public Subnets have a route to the internet gateway.
- NAT Gateways (AWS-managed) & NAT Instances (self-managed) allow your instances in your Private Subnet to access the internet while remaining private

### Network ACL & Security Groups
- NACL (Network ACL)
	- A firewall which controls traffic from and to subnets
	- Can have ALLOW and DENY rules
	- Are attached at the Subnet level
	- Rules only include IP addresses
- Security Groups
	- A firewall that controls traffic to and from an ENI / an EC2 Instance
	- Can have only ALLOW rules
	- Rules include IP addresses and other security groups

practice : 
- create VPC 
- create subnet
- create Security Groups

### VPC Flow Logs
- Capture information about IP traffic going into your interfaces:
	- VPC Flow Logs
	- Subnet Flow Logs
	- Elastic Network Interface Flow Logs
- Helps to monitor & troubleshoot connectivity issues. Example:
	- Subnets to internet
	- Subnets to subnets
	- Internet to subnets
- Captures network information from AWS managed interfaces too: Elastic Load Balancers, ElastiCache, RDS, Aurora, etc…
- VPC Flow logs data can go to S3 / CloudWatch Logs

### VPC Peering 
VPC Peering is a way for two VPCs to connect privately using the AWS network.
- Must not have overlapping CIDR (IP address ranges).
- Peering VPC connections are not transitive (must be established for each VPC that needs to communicate with each other)

practice :
- menghubungkan 2 VPC agar bisa saling berkomunikasi 

### VPC Endpoint
- Endpoints allow you to connect to AWS Services using a private network instead of the public wwwnetwork
- This gives you enhanced security and lower latency to access AWS services
- VPC Endpoint Gateway: S3 & DynamoDB
- VPC Endpoint Interface: the rest

### AWS PrivateLink 
the most secure and scalable way to expose services to multiple VPCs even up to 1000s of VPCs without the need for peering, route tables or anything else.
By requiring a load balancer for VPC services and ENI for VPC customers


### Site to Site VPN & Direct Connect
- Site to Site VPN
	- Connect an on-premises VPN to AWS
	- The connection is automatic encrypted
	- Goes over the public internet
- Direct Connect (DX)
	- Establish a physical connection between on-premises and AWS
	- The connection is private, secure and fast
	- Goes over a private network
	- Takes at least a month to establish


### AWS Client VPN
- Connect from your computer using OpenVPN to your private network in AWS and on-premises
- Allow you to connect to your EC2 instances over a private IP (just as if you were in the private VPC network)
- Goes over public Internet

### Transit Gateway 
- For having transitive peering between thousands of VPC and on-premises, hub-and-spoke (star) connection
- One single Gateway to provide this functionality
- Works with Direct Connect Gateway, VPN connections

## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1618910462984458240)
