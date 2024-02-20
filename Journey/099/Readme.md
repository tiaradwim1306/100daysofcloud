# More Solutions Architectures & WhitePapers and Architectures : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

# Cloud Research
## More Solutions Architecture
### Event Processing in AWS - Lambda, SNS & SQS
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/29143ace-8787-4d84-88f4-98c4bf7e1310)

bagaimana jika kita ingin mengirim message ke multiple SQS, dari aplikasi langsung ke SQS secara bergantian bisa namun nanti akan terjadi crash sehingga kita bisa menggunakan SNS sebagai penghubung ditengahnya yang fungsinya untuk menjembatani message dari aplikasi ke SQS. System ini disebut Fan Out Pattern.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/414ed074-44fc-4dfa-ac0b-66d2cba3ba20)

### S3 Event Notifications
notification bisa berisi S3:ObjectCreated, S3:ObjectRemoved, S3:ObjectRestore, S3:Replication, etc. BIsa menggunakan object name filtering seperti (*.jpg). Kita bisa membuat banyak S3 event yang kita inginkan, bisa menggunakan SNS,SQS, atapun lambda. S3 event notifications biasanya mengirim event dalam hitungan detik but sometimes take a minute or longer.
> Use case :  generate thumbnails of images uploaded to S3

### S3 Event Notifications with Amazon EventBridge
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/a6327c6f-b4fb-45c6-9ce9-cc2f2d592f5a)

- Advanced filtering options with JSON rules (metadata, object size, name...), 
- Multiple Destinations – ex Step Functions, Kinesis Streams / Firehose…
- EventBridge Capabilities – Archive, Replay Events, Reliable delivery

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/8bbdb016-ef2e-4f3b-99a3-700ecc479ed1)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/93d4a9cb-d2f3-48ff-986f-43fec71a2cab)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/6b6d6396-d612-42af-8318-f8331f136971)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/521476f7-c848-4a62-bb69-e41a771b17ad)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/cac7f56f-9158-4e3e-8f34-da90233ab270)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/8c0e6d64-f75e-4d5c-8a2e-4004c23719f5)

### High Performance Computing (HPC)
cloud is perfect place to perform HPC, create a very high number of resources in no time.  can speed up time to results by adding more resources and pay only for the systems you have used.
> Perform genomics, computational chemistry, financial risk modeling, weather prediction, machine learning, deep learning, autonomous driving

### Data Management & Transfer
- AWS Direct Connect : Move GB/s of data to the cloud, over a private secure network
- Snowball & Snowmobile : Move PB of data to the cloud 
- AWS DataSyn : Move large amount of data between on-premises and S3, EFS, FSx for Windows

### Compute and Networking
- EC2 Instances : CPU optimized, GPU optimized and Spot Instances / Spot Fleets for cost savings + Auto Scaling.
- EC2 Placement Groups : Cluster for good network performance

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1f02a678-5194-4d34-9a02-23cc0b964879)

- EC2 Enhanced Networking (SR-IOV) : Higher bandwidth, higher PPS (packet per second), lower latency. Option 1: Elastic Network Adapter (ENA) up to 100 Gbps. Option 2: Intel 82599 VF up to 10 Gbps – LEGACY.
- Elastic Fabric Adapter (EFA) : Improved ENA for HPC, only works for Linux. Great for inter-node communications, workloads yang sangat erat. Leverages Message Passing Interface (MPI) standard. Bypasses the underlying Linux OS to provide low-latency, reliable transport.

### Storage
- Instance-attached storage :
  - EBS : scale up to 256,000 IOPS with io2 Block Express
  - Instance Store: scale to millions of IOPS, linked to EC2 instance, low latency

- Network storage :
  - Amazon S3: large blob, not a file system
  - Amazon EFS: scale IOPS based on total size, or use provisioned IOPS
  - Amazon FSx for Lustre : HPC optimized distributed file system, millions of IOPS, Backed by S3.

### Automation and Orchestration
- AWS Batch : 
  - AWS Batch supports multi-node parallel jobs, which enables you to run single jobs that span multiple EC2 instances.
  - Easily schedule jobs and launch EC2 instances sesuai kebutuhan.

- AWS ParallelCluster : 
  - Open-source cluster management tool to deploy HPC on AWS
  - Configure with text files
  - Automate creation of VPC, Subnet, cluster type and instance types
  - Ability to enable EFA on the cluster (improves network performance)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/bec14a42-598d-468c-aba4-529d2dde2b49)

## White Papers & Architectures
- Well Architected Framework Whitepaper 
- Well Architected Tool 
- AWS Trusted Advisor 
- Reference architectures resources (for real -world) 
- Disaster Recovery on AWS Whitepaper

### Well Architected Framework General Guiding Principles 
→ https://aws.amazon.com/architecture/well-architected/ 
Stop guessing your capacity needs, Test systems at production scale, Automate to make architectural experimentation easier. Allow for evolutionary architectures, Drive architectures using data, Improve through game days

### 6 Pillars Well Architected Framework
1. Operational Excellence
2. Security
3.  Reliability
4. Performance Efficiency
5. Cost Optimization
6. Sustainability
> They are not something to balance, or trade-offs, they’re a synergy

### AWS Well-Architected Tool
free tool to <b>review your architectures</b> against the 6 pillars Well-Architected Framework and <b>adopt architectural best practices.</b>
How does it work? Select your workload and answer questions, Review your answers against the 6 pillars, Obtain advice: get videos and documentations, generate a report, see the results in a dashboard.
let’s have a look :  https://console.aws.amazon.com/wellarchitected 

### Trusted Advisor 
No need to install anything – high level AWS account assessment, Analyze your AWS accounts and provides recommendation on 5 categories.
- Cost optimization 
- Performance 
- Security
- Fault tolerance
- Service limits

### Support Plans
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1f17e2de-cb57-4f7f-9320-5df120d86353)

### More Architecture Examples
Kami telah menjelajahi pola arsitektur yang paling penting : 
- Classic: EC2, ELB, RDS, ElastiCache, etc…
- Serverless: S3, Lambda, DynamoDB, CloudFront, API Gateway, etc…

> if u want to see more AWS architecture : https://aws.amazon.com/architecture/ , https://aws.amazon.com/solutions/ 

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1759849715997483384)



