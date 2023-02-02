
# Security & Compliance Part 1 : Course on Udemmy by Stepahane Mareek

## Cloud Research


## AWS Shared Responsibility Model
- AWS responsibility - Security of the Cloud
- Customer responsibility - Security in the Cloud
- Shared controls:Patch Management, Configuration Management, Awareness & Training 

### Shared Responsibility Model for RDS
- AWS responsibility:
	- Manage the underlying EC2 instance, disable SSH access
	- Automated DB patching
	- Automated OS patching
	- Audit the underlying instance and disks & guarantee it functions
- Your responsibility:
	- Check the ports / IP / security group inbound rules in DB’s SG
	- In-database user creation and permissions
	- Creating a database with or without public access
	- Ensure parameter groups or DB is configured to only allow SSL connections
	- Database encryption setting

### Shared Responsibility Model for S3
- AWS responsibility: 
	- Guarantee you get unlimited storage 
	- Guarantee you get encryption 
	- Ensure separation of the data between different customers 
	- Ensure AWS employees can’t access your data 
- Your responsibility: 
	- Bucket configuration 
	- Bucket policy / public setting 
	- IAM user and roles 
	- Enabling encryption

## DDOS (Distributed Denial-of-Service)

attacks carried out by hackers by sending many requests to the server so that when normal users want to access the server they cannot because many people access server.

### AWS Shield 
- AWS Shield Standard:
	- Free service that is activated for every AWS customer
	- Provides protection from attacks such as SYN/UDP Floods, Reflection attacks and other layer 3/layer 4 attacks
- AWS Shield Advanced:
	- Optional DDoS mitigation service ($3,000 per month per organization)
	- Protect against more sophisticated attack on Amazon EC2, Elastic Load Balancing (ELB), Amazon CloudFront, AWS Global Accelerator, and Route 53
	- 24/7 access to AWS DDoS response team (DRP)
	- Protect against higher fees during usage spikes due to DDoS

### AWS WAF (Web Application Firewall)
Protects your web application from common web exploits at layer 7 such as HTTP

Define Web ACL (Web Access Control List):
- Rules can include IP addresses, HTTP headers, HTTP body, or URI strings
- Protects from common attack - SQL injection and Cross-Site Scripting (XSS)
- Size constraints, geo-match (block countries)
- Rate-based rules (to count occurrences of events) – for DDoS protection

2 types of encryption:
- at rest : data is stored or archived on the device (RDS,S3 Glacier Deep Archive, etc.
- In transit (moving): data is moved from one location to another

### KMS 
Encryption service in AWS is KMS (Key Management Service),KMS manages encryption keys for us

### CloudHSM
is a service that provides encryption hardware and you can manage your own encryption keys completely and tamper-resistant.

### Types of Customer Master Keys : CMK
- Customer Managed CMK:
Create, manage and use by customers, can enable or disable, updated annually and keys can be brought by yourself

- AWS managed CMK:
Created, managed and used on the customer’s behalf by AWS and used by AWS services (aws/s3, aws/ebs, aws/redshift)

- AWS owned CMK:
Collection of CMKs that an AWS service owns and manages to use in multiple accounts and used to protect the resources in your account.

- CloudHSM key (custom keystore):
Keys are generated from your own CloudHSM hardware and cryptographic operations are performed within the CloudHSM cluster


### AWS Certificate Manager (ACM) 
service used to easily provision, manage, and deploy SSL/TLS Certificates.
- provides in-flight encryption for websites (HTTPS)
- Support public and private TLS certificates, free for public TLS certificates
- Automatic TLS certificate renewal


## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1621054627994271744)
