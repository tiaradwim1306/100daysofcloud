
#  Global Infrastructure : Course on Udemmy by Stepahane Mareek

## Cloud Research
### Global Application 
A global application is an application deployed in multiple Regions or Edge Locations for decreased latency.
The function for  disaster recovery (DR).
More secure because distributed global infrastructure is harder to attack 

nb : Latency is the time it takes for a network packet to reach a server

global infrastructure :
- Regions: For deploying applications and infrastructure
- Availability Zones: Made of multiple data centers
- Edge Locations (Points of Presence): for content delivery as close as possible to users

Global Application in AWS
- Global DNS : Amazon 53
- Global Content Delivery Network (CDN): CloudFront
- S3 Transfer Acceleration
- AWS Global Accelerator

### Amazon 53
this service managed DNS (Domain Name System),cost = 12$/year,
most common records are:
- A
- AAAA
- CNAME 
- Alias 

Routing policies :
- simple routing policy
- weighted routing policy 
- latency routing policy
- failover routing policy 

### CloudFront
Content Delivery Network (CDN), which improves read performance, content is cached at the edge, improves user experience and DDoS Protection

CloudFront vs S3 Cross Region Replication
- CloudFront:
	- Global Edge network
	- Files are cached for a TTL (maybe a day)
	- Great for static content that must be available everywhere
- S3 Cross Region Replication:
	- Must be setup for each region you want replication to happen
	- Files are updated in near real time
	- Read only
	- Great for dynamic content that needs to be available at low-latency in some regions

### S3 Transfer Acceleration
Increase transfer speed by transferring file to an AWS edge location which will forward the data to the S3 bucket in the target region

tools : [klik here](https://s3-accelerate-speedtest.s3-accelerate.amazonaws.com/en/accelerate-speed-comparsion.html)

### AWS Global Acceleration
Improve global application availability and performance using the AWS global network to optimize routes to your applications (60% increase).

tools : [klik here](https://speedtest.globalaccelerator.aws/#/) 

AWS Global Accelerator vs CloudFront
- They both use the AWS global network and its edge locations around the world
- Both services integrate with AWS Shield for DDoS protection.
- CloudFront – Content Delivery Network
	- Improves performance for your cacheable content (such as images and videos)
	- Content is served at the edge
- Global Accelerator
	- No caching, proxying packets at the edge to applications running in one or more AWS Regions.
	- Improves performance for a wide range of applications over TCP or UDP
	- Good for HTTP use cases that require static IP addresses
	- Good for HTTP use cases that required deterministic, fast regional failover


### AWS Outposts
AWS Outposts is a service that can be used for Hybrid Cloud, AWS Outposts is a "server rack" that offers the same AWS infrastructure, services, APIs & tools to build your own applications on-premises as in the cloud and you are responsible for the physical security of Outposts Rack

Benefits:
- Low-latency access to on-premises systems
- Local data processing
- Data residency
- Easier migration from on-premises to the cloud
- Fully managed service

service that work on Outposts: EC2, EBS, S3, EKS, ECS, RDS, EMR 

### AWS WaveLength
- WaveLength Zones are infrastructure deployments embedded within the telecommunications providers' datacenters at the edge of the 5G networks
- Ultra-low latency applications through 5G networks, example: EC2, EBS, VPC, etc.
- Traffic doesn't leave the Communication Service Provider's (CSP) network
- High-bandwidth and secure connection to the parent AWS Regionand no additional charges or service agreements
- Use cases: Smart Cities, ML-assisted diagnostics, Connected Vehicles, Interactive Live Video Streams,AR/VR, Real-time Gaming

### AWS Local Zones
Places AWS compute, storage, database,and other selected AWS services closer to end users to run latency-sensitive applications

example :
- AWS Region: N. Virginia (us-east-1)
- AWS Local Zones: Boston, Chicago, Dallas,Houston, Miami, …

### Global Application Architecture 
- Single region,single AZ -> high availibility X,global latency X
- Single region,multi AZ -> high availibility √,global latency X
- Multi region,active-passive -> Global Reads’ Latency √, Global Writes’ Latency X
- Multi Region, Active-Active -> Global Reads’ Latency √, Global Writes’ Latency √


## Social Proof


[Twitter](https://twitter.com/tiaradwim1306/status/1618043985297313794)
