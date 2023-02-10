
# Pricing Models in AWS : Course on Udemmy by Stepahane Mareek


## Cloud Research
### Pricing Models in AWS
AWS has 4 pricing models :
- pay as you go 
- save when you reserve
- pay less by using more
- pay less as AWS grows 

### Pricing for service 

#### Compute Pricing 
EC2 :
- Only charged for what you use 
- Number of instances 
- Instance configuration (physical capacity,region,OS and software,instance type and instance size)
- ELB running time and amount of data processed 
- Detailed monitoring

Lambda : 
- Pay per call 
- Pay per duration 

ECS : 
- EC2 Launch Type Model: No additional fees, you pay for AWS resources stored and created in your application

Fargate :
- Fargate Launch Type Model: Pay for vCPU and memory resources allocated to your applications in your containers

#### Storage Pricing 
S3 :
- Storage class: S3 Standard, S3 Infrequent Access, S3 One-Zone IA, S3 Intelligent Tiering, S3 Glacier and S3 Glacier Deep Archive
- Number and size of objects: Price can be tiered (based on volume)
- Number and type of requests
- Data transfer OUT of the S3 region
- S3 Transfer Acceleration
- Lifecycle transitions
- Similar service: EFS (pay per use, has infrequent access & lifecycle rules)

EBS :
- Volume type (based on performance) 
- Storage volume in GB per month provisionned 
- IOPS: 
	- General Purpose SSD: Included 
	- Provisioned IOPS SSD: Provisionned amount in IOPS 
	- Magnetic: Number of requests 
- Snapshots: 
	- Added data cost per GB per month 
- Data transfer: 
	- Outbound data transfer are tiered for volume discounts 
	- Inbound is free

RDS :
- Per hour billing
- Database characteristics : Engine, Size, Memory class
- Purchase type: On-demand, Reserved instances (1 or 3 years) with required up-front
- Backup Storage: There is no additional charge for backup storage up to 100% of your total database storage for a region. 
- Additional storage (per GB per month) 
- Number of input and output requests per month 
- Deployment type (storage and I/O are variable) : Single AZ, Multiple AZs 
- Data transfer : 
	- Outbound data transfer are tiered for volume discounts 
	- Inbound is free

#### Content Delivery 
CloudFront : 
- Pricing is different across different geographic regions 
- Aggregated for each edge location, then applied to your bill 
- Data Transfer Out (volume discount) 
- Number of HTTP/HTTPS requests


## Social Proof


[Twitter](https://twitter.com/tiaradwim1306/status/1624060863085961218)
