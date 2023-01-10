
# EC2 PART 2 : Course on Udemmy by Stepahane Mareek


## Cloud Research

### EC2 Instance Types
- General Purpose
- Compute Optimized
- Memory Optimized
- Storage Optimized 

### Security Groups
Security groups control how traffic is allowed in or out of  EC2 Instances.
- securiry groups like a firewall on EC2 instances 
- The security group contains only allowed rules
- Security group rules can be referenced by IP or security group

Security groups manage things like :
- Access to Ports  
- Authorised IP ranges – IPv4 and IPv6 
- Control of inbound network (from other to the instance) 
- Control of outbound network (from the instance to other)

port and meaning :
- 22 = SSH (Secure Shell) - log into a Linux instance
- 21 = FTP (File Transfer Protocol) – upload files into a file share
- 22 = SFTP (Secure File Transfer Protocol) – upload files using SSH
- 80 = HTTP – access unsecured websites
- 443 = HTTPS – access secured websites
- 3389 = RDP (Remote Desktop Protocol) – log into a Windows instance

EC2 on demand :
- Pay for what you use:
	- Linux or Windows - billing per second, after the first minute
	- All other operating systems - billing per hour
- Have the highest cost but no upfront payment
- No long-term commitment
- Recommended for short-term and un-interrupted workloads, where you can't predict how the application will behave

### Shared Responsibility Model for EC2
- AWS = RESPONSIBILITY FOR THE SECURITY OF THE CLOUD
	- Infrastructure (global network security)
	- Isolation on physical hosts
	- Replacing faulty hardware
	- Compliance validation
- CUSTOMER = RESPONSIBILITY FOR THE SECURITY IN THE CLOUD
	- Security Groups rules
	- Operating-system patches and updates
	- Software and utilities installed on the EC2 instance
	- IAM Roles assigned to EC2 & IAM user access management
	- Data security on your instance

## EC2 SUMMARY
- EC2 consists of AMI (OS), size (CPU + RAM), storage, security groups and user data
- Security group such as firewall on EC2 instances
- User Data is the script that is launched on the first start of the instance
- SSH is a one way remote instance tool with CLI
ex : windows - windows powershell
- Purchase Options : On Demand, Spot, Ordered (Standard + Conversion + Scheduled), Dedicated Host, Dedicated Instance


## Social Proof

[Twitter](https://mobile.twitter.com/tiaradwim1306/status/1612752359867944961)
