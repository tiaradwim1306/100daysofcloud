
# EC2 Instance Storage (EC2 Image Builder,EC2 Instance Store,EFS) & ELB and ASG  : Course on Udemmy by Stepahane Mareek

## Cloud Research
### EC2 Image Builder 
the function is to automate the creation, maintain, validate and test EC2 AMIs on a scheduled basis (weekly, when packages update, etc...)

### EC2 Instance Store
EBS has limited performance, if you need higher performance hardware disk use EC2 Instance Store with better I/O performance

### ## EFS (Elastic File System)
NFS can be installed on around 100s of EC2 and works with EC2 Linux instances in multiple Availability Zones.
Highly available, scalable, expensive (3x gp2), pay per use, no capacity planning

### Shared Responsibility Model for EC2 Storage

- AWS = RESPONSIBILITY FOR THE SECURITY OF THE CLOUD
	- Infrastructure
	- Replication for data for EBS volumes & EFS drives
	- Replacing faulty hardware
	- Ensuring their employees cannot access your data
- CUSTOMER = RESPONSIBILITY FOR THE SECURITY IN THE CLOUD
	- Setting up backup / snapshot procedures
	- Setting up data encryption
	- Responsibility of any data on the drives
	- Understanding the risk of using EC2 Instance Store

### Amazon FSx

- Launch 3rd party high-performance file systems on AWS
- Fully managed service
- Types : FSx for Lustre, FSx for Windows File Server, FSx for NetApp ONTAP

### ## EC2 Instance Storage - Summary
- EBS Volumes :
	- network drives attached to one EC2 instance at a time 
	- Mapped to an Availability Zones 
	- Can use EBS Snapshots for backups / transferring EBS volumes across AZ
- AMI: create ready-to-use EC2 instances with our customizations
- EC2 Image Builder: automatically build, test and distribute AMIs 
- EC2 Instance Store:
	- High performance hardware disk attached to our EC2 instance 
	- Lost if our instance is stopped / terminated
- EFS: network file system, can be attached to 100s of instances in a region 
- EFS-IA: cost-optimized storage class for infrequent accessed files 
- FSx for Windows: Network File System for Windows servers 
- FSx for Lustre: High Performance Computing Linux file system

## ELB (Elastic Load Balancing) & ASG (Auto Scalling Groups) 

### Scalability & high availibility 
there are 2 kinds of scalability :
- vertical scalability

Vertical scalability means increase in size and has limits (hardware limit), example from t2.micro to t2.large.
Very common for non-distributed systems, such as databases.
- horizontal scalability 

Horizontal scalability means increasing the number of instances/systems and implies a distributed system.
very common for web applications/modern applications.
This scalability is very easy to do thanks to the cloud offerings like Amazon EC2
- High Availability

High availability usually goes hand in hand with horizontal scaling, running instances in at least 2 AZ and goal is surviving data center loss (disaster)

### example :
- vertical scalability : t2.nano to l2tbl.metal
- horizontal scalability : auto scaling group,load balancer
- High Availability : auto scaling group multi AZ

### Load Balancing 
Load balancers are servers that forward internet traffic to multiple servers (EC2 Instances) downstream.

## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1614092741566423040)
