# Amazon VPC : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/34b70149-c113-418e-af2f-bfcd0152ff1f)

### CIDR – IPv4
Classless Inter-Domain Routing adalah metode for allocating IP addresses. digunakan untuk security group rules and AWS networking.

A CIDR consists of two components : 
- Base IP : Represents an IP contained in the range (XX.XX.XX.XX), Example: 10.0.0.0, 192.168.0.0, …
- SubnetMask : Defines how many bits can change in the IP, Example: /0, /24, /32. 

The Subnet Mask basically allows part of the underlying IP to get additional next values from the base IP.

#### Public vs. Private IP (IPv4)
Internet Assigned Numbers Authority (IANA) menetapkan blok alamat IPv4 tertentu untuk penggunaan alamat pribadi (LAN) dan publik (Internet). All the rest of the IP addresses on the Internet are Public.

#### Default VPC
All new AWS accounts have a default VPC. New EC2 instances are launched into the default VPC if no subnet is specified. Default VPC has Internet connectivity and all EC2 instances inside it have public IPv4 addresses. We also get a public and a private IPv4 DNS names.

You can have multiple VPCs in an AWS region (max. 5 per region – soft limit), Max. CIDR per VPC is 5, for each CIDR : 
- Min. size is /28 (16 IP addresses)
- Max. size is /16 (65536 IP addresses)

> Your VPC CIDR should NOT overlap with your other networks (e.g., corporate)

### Subnet
aws reserve 5 IP address in each subnet, These 5 IP addresses are not available for use and can’t be assigned to an EC2 instance.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/336d63c7-7a66-4c96-8a18-45538c515999)

jika kita membutuhkan 29 IP, tidak boleh menggunakan /27 krena 32 -5 = 27. Sehingga IP yang dibutuhkan kurang, sehingga gunakan /26 dengan jumlah IP 64 -5 = 59 dan itu sudah lebih dari range IP yang digunakan.

### Internet Gateway (IGW)
Allows resources (e.g., EC2 instances) in a VPC connect to the Internet and It scales horizontally and is highly available and redundant.
Dibuat secara terpisah dengan VPC, One VPC can only be attached to one IGW dan sebaliknya. 
> Route tables must also be edited!

### Bastion Hosts
We can use a Bastion Host to SSH into our private EC2 instances. The bastion is in the public subnet which is then connected to all other private subnets.

Bastion Host security group must allow inbound from the internet on port 22 from restricted CIDR, for example the public CIDR of your corporation. Security Group of the EC2 Instances must allow the Security Group of the Bastion Host, or the private IP of the Bastion host.

### NAT Instance (outdated, but still at the exam)
NAT (Network Address Translation), Allows EC2 instances in private subnets to connect to the Internet. Must be launched in a public subnet. Must disable EC2 setting: Source / destination Check. Must have Elastic IP attached to it. Route Tables must be configured to route traffic from private subnets to the NAT Instance

Pre-configured Amazon Linux AMI is available, Not highly available, Internet traffic bandwidth depends on EC2 instance type, must manage Security Groups & rules :
- inbound : Allow HTTP / HTTPS traffic coming from Private Subnets, Allow SSH from your home network (access is provided through Internet Gateway)
- outbound : Allow HTTP / HTTPS traffic to the Internet

### NAT Gateway
AWS-managed NAT, higher bandwidth, high availability, no administration.pay per hour for usage & bandwidth. NATGW is created in a specific Availability Zone, uses an Elastic IP.

Can’t be used by EC2 instance in the same subnet (only from other subnets), Requires an IGW (Private Subnet => NATGW => IGW).

#### NAT Gateway with High Availability
NAT Gateway is resilient within a single Availability Zone, Must create multiple NAT Gateways in multiple AZs for fault-tolerance. There is no cross-AZ failover needed because if an AZ goes down it doesn't need NAT

#### NAT Gateway VS NAT Instance

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/4ef4fbdb-f6e3-486d-832e-3dd8b45f03e8)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/bb70e3f9-3cb8-4ea4-a361-2d2dac85fdf7)

### Network Access Control List (NACL)
NACL seperti firewall yang mengontrol traffic from and to subnets, One NACL per subnet if new subnets are assigned the Default NACL. Newly created NACLs will deny everything and NACL adalah cara terbaik untuk blocking a specific IP address at the subnet level.
NACL Rules : 
- Rules have a number (1-32766), semakin kecil angkanya maka akan semakin diprioritaskan.
- First rule match akan menentukan keputusan.
- Example: if you define #100 ALLOW 10.0.0.10/32 and #200 DENY 10.0.0.10/32, the IP address will be allowed because 100 has a higher precedence over 200
- The last rule diberi tanda (*) and denies a request in case of no rule match
- AWS recommends adding rules dengan penambahan 100

#### Default NACL
Accepts everything inbound/outbound with the subnets it’s associated with. Jangan pernah modify the Default NACL, instead create custom NACLs.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/8bde6ac4-d474-4d04-9760-43ac999d5ca5)

### Ephemeral Ports
agar 2 endpoint bisa establish a connection mereka harus menggunakan port. Clients connect to a defined port, and expect a response on an ephemeral port (port sementara).
Different Operating Systems use different port ranges, examples :
- <b>IANA & MS Windows 10 → 49152 – 65535
- Many Linux Kernels → 32768 – 60999 </b>

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/37b18352-b26e-41a8-a349-be90395e2265)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/6bab06f3-5e76-4d04-a832-ca01e7890c50)

### Security Group vs. NACLs

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/92ba49c0-60ed-433b-9cb5-a085068bfc1c)

### VPC Peering

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/af0c3c64-558c-4a14-ac75-86eaec1298dd)

Privately connect two VPCs using AWS network and make them behave as if they were in the same network. Must not have overlapping CIDRs.
VPC Peering connection is NOT transitive (must be established for each VPC that need to communicate with one another).

> You must update route tables in each VPC’s subnets to ensure EC2 instances can communicate with each other.

You can create VPC Peering connection between VPCs in different AWS accounts/regions and can reference a security group in a peered VPC (works cross accounts – same region)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/b661662e-9e15-4900-aca0-7a645698d1e7)

### VPC Endpoints (AWS PrivateLink)
Every AWS service is publicly exposed (public URL) and PC Endpoints (powered by AWS
PrivateLink) allows you to connect to AWS services using a private network instead of using the public Internet.

They’re redundant and scale horizontally and don't need GW, NATGW, etc to access AWS Services. In case of issues:
- Check DNS Setting Resolution in your VPC
- Check Route Tables

#### Types of Endpoints : 
Interface Endpoints (powered by PrivateLink) : 
- Provisions an ENI (private IP address) as an entry point (must attach a Security Group)
- Supports most AWS services
- $ per hour + $ per GB of data processed
> example : kita ingin menghubungkan EC2 instance dengan Amazon SNS menggunakan interface VPC Endpoint.

Gateway Endpoints : 
- Provisions a gateway and must be used as a target in a route table (does not use security groups)
- Supports both S3 and DynamoDB
- Free 
> example : kita ingin menghubungkan S3 atau DynamoDB ke instance kita, bisa menggunakan Gateway VPC endpoint.

#### Gateway or Interface Endpoint for S3?
gateway mungkin lebih preferred daripada interface karena gateway bersifat gratis. 
Interface Endpoint adalah akses pilihan yang diperlukan dari on-promises. (Site to Site VPN or Direct Connect), a different VPC or a different region

#### Lambda in VPC accessing DynamoDB
DynamoDB is a public service from AWS, 
- Option 1 - Access from the public internet : Because Lambda is in a VPC, it needs a NAT Gateway in a public subnet and an internet gateway
- Option2 - Access from the private VPC network : Deploy a VPC Gateway endpoint for DynamoDB and Change the Route Tables

### VPC Flow Logs
Capture information about IP traffic going into you interfaces: VPC Flow Logs, Subnet Flow Logs, Elastic Network Interface (ENI) Flow Logs.
Helps to monitor & troubleshoot connectivity issues. Flow logs data can go to S3, CloudWatch Logs, and Kinesis Data Firehose.
Captures network information from AWS managed interfaces too: ELB, RDS, ElastiCache, Redshift, WorkSpaces, NATGW, Transit Gateway...

#### VPC Flow Logs Syntax

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/b6383326-b2d8-4d7f-b2c7-e894dcddf748)

- srcaddr & dstaddr – help identify problematic IP
- srcport & dstport – help identity problematic ports
- Action – success or failure of the request due to Security Group / NACL
- Can be used for analytics on usage patterns, or malicious behavior
- Query VPC flow logs using Athena on S3 or CloudWatch Logs Insights
- Flow Logs examples: https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-records-examples.html

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/63f03a75-e864-43bd-b5fd-f87a375ae209)

### AWS Site-to-Site VPN
Virtual Private Gateway (VGW)
- VPN concentrator on the AWS side of the VPN connection
- VGW is created and attached to the VPC tempat Anda ingin membuat Site-to-Site VPN connection
- Possibility to customize the ASN (Autonomous System Number)

Customer Gateway (CGW)
- Software application or physical device on customer side of the VPN connection
- https://docs.aws.amazon.com/vpn/latest/s2svpn/your-cgw.html#DevicesTested

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/3797ec3c-cd94-49cb-8d4c-402f60cb26df)

Bagaimana cara membuat konektivitas antara CGW dan VGW? kita akan menggunakan IP address Public milik client lalu akan di connectkan ke Virtual Private Gateway.If it’s behind a NAT device that’s enabled for NAT traversal (NAT-T), use the public IP address of the NAT device.
> Important step: enable Route Propagation for the Virtual Private Gateway in the route table that is associated with your subnets.

If you need to ping your EC2 instances from on-premises, make sure you add the ICMP protocol on the inbound of your security groups

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1e54b39e-0e2a-4e2b-8f60-cdfcc1c3c4f6)

- Provide secure communication between multiple sites, if you have multiple VPN
connections.
- low-cost hub and spoke model for primary or secondary network connectivity between different locations (VPN only)
- It’s a VPN connection so it goes over the public Internet
- To set it up, connect multiple VPN connections on the same VGW, setup dynamic routing and configure route tables.

### Direct Connect (DX)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/e27474db-2389-48b9-b62d-ff888dec6fdc)

provides a dedicated private connection from a remote network to your VPC, dedicated connection must be setup between your DC and AWS Direct Connect locations. Supports both IPv4 and IPv6. need to setup a Virtual private gateway di VPC, access public resource (S3) and private (EC2) on same connection. Use Case : 
- Increase bandwidth throughput - working with large data sets – lower cost
- More consistent network experience - applications using real-time data feeds
- Hybrid Environments (on prem + cloud)

> If you want to setup a Direct Connect to one or more VPC in many different regions (same account), you must use a Direct Connect Gateway.

#### Connection Types : 
- Dedicated Connections : 1Gbps,10 Gbps and 100 Gbps capacity
Physical ethernet port dedicated to a customer and Request made to AWS first, then completed by AWS Direct Connect Partners.
- Hosted Connections: 50Mbps, 500 Mbps, to 10 Gbps
Connection requests are made via AWS Direct Connect Partners, Capacity can be added or removed on demand. 1, 2, 5, 10 Gbps available at select AWS Direct Connect Partners.

> waktu tunggu kadang lebih lama dari 1 bulan untuk membuat new connection

#### Encryption
Data in transit not encrypted but is private, AWS Direct Connect + VPN provides an IPsec-encrypted private connection. Good for an extra level of security,namun sedikit lebih rumit untuk diterapkan.

#### Resiliency

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1dec3b0c-b53e-43eb-9602-225ecd6e58ae)

### Site-to-Site VPN connection as a backup
In case Direct Connect fails, you can set up a backup Direct Connect connection (expensive) ,or a Site-to-Site VPN connection.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/ffc851e5-60bd-4e8a-8000-5744918a9c23)

### Transit Gateway

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/68f42f44-0eda-4a4e-acb7-1948d87bce6e)

Bagaimana jika kita ingin menghubungkan banyak VPC atau on promises, tidak mungkin kita menghubungkan mereka dengan peering ataupun VPN satu-satu. Untuk itu AWS menghadirkan transit gateway yang menjadi solusi untuk masalah ini.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/451c2f95-bec9-495b-a77d-1ba428edd3f6)

For having transitive peering between thousands of VPC and on-premises, hub-and-spoke (star) connection. Regional resource and can work cross-region.
Share cross-account using Resource Access Manager (RAM), can peer Transit Gateways across regions. Works with Direct Connect Gateway, VPN connections, support IP Multicast (not supported by any other AWS service).
> Route Tables: limit which VPC can talk with other VPC.

### IP Multicast (not supported by any other AWS service)
ECMP = Equal-cost multi-path routing, Routing strategy to allow meneruskan packet melalui beberapa jalur terbaik. 
> use case : create multiple Site-to-Site VPN connections to increase the bandwidth of your connection to AWS

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/84a803ca-7dc4-4f3d-a801-2ae28f63393d)

### Traffic Mirroring
allow you to capture and inspect network traffic in your VPC, Route the traffic to security appliances that you manage.
Capture the traffic dengan menentukan from (source traffic) dan to (targets traffic). Kita bisa menentukan semua packet atau packet apa saja yang ingin kita capture. Source and Target can be in the same VPC or different VPCs (VPC Peering).
> Use cases: content inspection, threat monitoring (pemantauan ancaman), troubleshooting, ..

### IPV6 
What is IPv6?

IPv4 designed to provide 4.3 Billion addresses dan mungkin akan segera habis, sehingga muncul IPV6 datang untuk meneruskan IPV4. Every IPv6 address is public and Internet-routable (no private range).
> example : 2001:db8:3333:4444:5555:6666:7777:8888, 2001:db8::, 2001:db8::1234:5678

#### IPv6 in VPC
IPv4 cannot be disabled for your VPC and subnets tapi kita bisa enable dan disable IPv6 (they’re public IP addresses) to operate in dual-stack mode.
Your EC2 instances will get at least a private internal IPv4 and a public IPv6 and They can communicate using either IPv4 or IPv6 to the internet through an Internet Gateway.

#### Troubleshooting
IPv4 cannot be disabled for your VPC and subnets, sehingga jika kita tidak bisa launch EC2 instance di subnet dikarenakan tidak dapat memperoleh IPv6 (the space is very large) ataupun karena tidak tersedia IPv4 di subnet Anda.
> Solution: create a new IPv4 CIDR in your subnet

#### Egress-only Internet Gateway
used for IPV6 only, (similar to a NAT Gateway but for IPv6). Allows instances in your VPC outbound connections melalui IPV6 sekaligus mencegah internet to initiate an IPv6 connection to your instances.
> must update the route table.

### Network Protection on AWS
service yang bisa digunakan untuk protect network on AWS : 
- Network Access Control Lists (NACLs)
- Amazon VPC security groups
- AWS WAF (protect against malicious requests)
- AWS Shield & AWS Shield Advanced
- AWS Firewall Manager (to manage them across accounts)

but, bagaimana jika kita ingin melindungi seluruh VPC kita dengan cara yang canggih? gunakan AWS Network Firewall

### AWS Network Firewall
protect seluruh VPC, From Layer 3 to Layer 7 protection and Arah mana pun, Anda dapat memeriksanya.
- VPC to VPC traffic
- Outbound to internet
- Inbound from internet
- To / from Direct Connect & Site-to-Site VPN

secara internal, the AWS Network Firewall uses the AWS Gateway Load Balancer dan rules bisa bersifat terpusat.

#### Fine Grained Controls
- Support 1000s of rules : IP & port, Protocol, Stateful domain list rule groups: only allow outbound traffic to *.mycorp.com or third-party software repo, Pencocokan pola umum menggunakan regex.
- Traffic filtering: Allow, drop, or alert for the traffic that matches the rules
- Inspeksi aliran aktif untuk melindungi terhadap ancaman jaringan dengan kemampuan pencegahan intrusi (seperti Gateway Load Balancer, namun semuanya dikelola oleh AWS)
- Send logs of rule matches to Amazon S3, CloudWatch Logs, Kinesis Data Firehose


## SUMMARY

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/99ffa717-5fab-4eb6-a615-6038975c56c6)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/ec6afab9-3626-4cc4-9a6a-c42a7607367d)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/9b3dcc58-ad42-45b9-91d9-961d83bcdb25)

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1752255538799530304)














