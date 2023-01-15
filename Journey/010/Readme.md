
# Amazon S3 : Course on Udemmy by Stepahane Mareek

## Cloud Research

### introduction to Amazon S3
Amazon S3 is ”infinitely scaling” storage,many websites and service use S3 as backbone and as an integration as well.

### Amazon S3 Use cases 
- Backup and storage 
- Disaster Recovery 
- Archive 
- Hybrid Cloud storage 
- Application hosting 
- Media hosting 
- Data lakes & big data analytics 
- Software delivery 
- Static website

### Bucket 
- Amazon S3 allows people to store objects (files) in “buckets” (directories)
- Buckets are defined at the region level and must have a globally unique name
- S3 is global service but buckets are created in a region

### Amazon S3 - Objects
- Objects (files) have a Key
- The key is the FULL path
- The key is composed of prefix + object name
- There’s no concept of “directories” within buckets
- Just keys with very long names that contain slashes (“/”)

### object 
- Object values are the content of the body,max size is 5TB 
- Metadata
- Tags
- Version ID 

### S3 Security 
- User based : IAM Policies
- Resource based : Bucket Policies,Object Access Control List (ACL),Bucket Access Control List (ACL) 

### S3 Static Website Hosting 
- S3 can host static websites and have them accessible on the Internet
- If you get a 403 Forbidden error, make sure the bucket policy allows public reads

### Amazon S3 -Versioning
- You can version your files in Amazon S3 and it's enabled at the bucket level
- Protect against unintended deletes and easy roll back to previous version
- Suspending versioning does not delete the previous versions

### Amazon S3 – Replication (CRR & SRR)
- Must enable Versioning in source and destination buckets
	- Cross-Region Replication (CRR)
	- Same-Region Replication (SRR)
- Buckets can be in different AWS accounts
- Must give proper IAM permissions to S3
- use cases :
	- CRR – compliance, lower latency access, replication across accounts
	- SRR – log aggregation, live replication between production and test accounts


### S3 Storage Classes 
- Amazon S3 Standard - General Purpose
- Amazon S3 Standard-Infrequent Access (IA)
- Amazon S3 One Zone-Infrequent Access
- Amazon S3 Glacier Instant Retrieval
- Amazon S3 Glacier Flexible Retrieval
- Amazon S3 Glacier Deep Archive
- Amazon S3 Intelligent Tiering

### S3 Encryption
- No Encryption
- Server-Side Encryption 
- Client-Side Encryption

### AWS Snow Family
- Highly-secure, portable devices to collect and process data at the edge, and migrate data into and out of AWS
- Data migration : Snowcone,Snowball Edge,Snowmobile
- Edge computing : Snowcone,Snowball Edge

### Hybrid Cloud for Storage 
- AWS is pushing for ”hybrid cloud”,part of your infrastructure are on-premises and on the cloud 
- This may be due to long cloud migration, security requirements, compliance requirements, IT strategy

### AWS Storage Gateaway 
- Bridge between on-premise data and cloud data in S3
- Hybrid storage service to allow on-premises to seamlessly use the AWS Cloud
- Use cases: disaster recovery, backup & restore, tiered storage
- Types of Storage Gateways: File Gateways,Gateway Volumes,Tape Gateways

## practice :
- create bucket and try to upload file or create folder
- create a bucket policy with the aws policy generator and make sure our files are accessible on the internet
- create static website hosting and make sure we can access our website
- enable bucket versioning, and we can see the changes when we upload the same file and make sure we can also go back to the previous version quickly
- create a replication rule from the bucket that we have created and make sure every time we upload a file in the original bucket, the replica bucket will copy it immediately

## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1614438248767705089)
