
# 6 Pillar Well Architected Framework : Course on Udemmy by Stepahane Mareek

## Introduction
6 Pillars Well Architected Framework :
1) Operational Excellence
2) Security
3) Reliability
4) Performance Efficiency
5) Cost Optimization
6) Sustainability

## Cloud Research
### 1) Operational Excellence
Includes the ability to run and monitor systems to deliver business value and to continually improve supporting processes and procedures

#### Design Principles :
- Perform operations as code - Infrastructure as code
- Annotate documentation - Automate the creation of annotated documentation after every build
- Make frequent, small, reversible changes - So that in case of any failure, you can reverse it
- Refine operations procedures frequently - And ensure that team members are familiar with it
- Anticipate failure
- Learn from all operational failures

#### AWS services used for operational excellence :
- prepare	: AWS CloudFormation, AWS Config
- operate	: AWS CloudFormation, AWS Config, AWS CloudTrail, CloudWatch, AWS X-Ray
- evolve	: AWS CloudFormation, AWS CodeBuild, AWS CodeCommit, AWS CodeDeploy, AWS CodePipeline

### 2) Security
Includes the ability to protect information, systems, and assets while deliverin business values through risk assessments and mitigation strategies

#### Design Principles :
- Implement a strong identity foundation - Centralize privilege management and reduce (or even eliminate) reliability on long-term credentials - Principle of least privilege - IAM
- Enable traceability - Integrate logs and metrics with systems to automatically respond and take action
- Apply security at all layers - Like edge network, VPC, subnet, load balancer, every instance, operating system, and application
- Automate security best practices
- Protect data in transit and at rest - Encryption, tokenization, and access control
- Keep people away from data - Reduce or eliminate the need for direct or manual access processing of data
- Prepare for security events - Run incident response simulations and use tools with automation to increase your speed for detection, investigation, and recovery
- Shared Responsibility Model

#### AWS services used for security :
- Identity and Access Management	: IAM, AWS-STS, MFA token, AWS Organizations
- Detective Controls			: AWS Config, AWS CloudTrail, Amazon CloudWatch
- Infrastructure Protection		: Amazon CloudFront, Amazon VPC, AWS Shield, AWS WAF, Amazon Inspector
- Data Protection				: KMS, S3, Elastic Load Balancing (ELB), Amazon EBS, Amazon RDS
- Incident Response			: IAM, AWS CloudFormation, Amazon CloudWatch Events


### 3) Reliability
Ability of a system to recover from infrastructure or service disruptions,dynamically acquire computing resources to meet demand, and mitigate disruptions such as misconfigurations or transient network issues

#### Design Principles :
- Test recovery procedures - Use automation to simulate different failures or to recreate scenarios that led to failures before
- Automatically recover from failure - Anticipate and remediate failures before they occur
- Scale horizontally to increase aggregate system availability - Distribute requests across multiple, smaller resources to ensure that they don't share a common point of failure
- Stop guessing capacity - Maintain the optimal level to satisfy demand without over or under provisioning - Use Auto Scaling
- Manage change in automation - Use automation to make changes to infrastructure

#### AWS services used for reliability :
- Foundations : IAM, VPC, Service limit, AWS Trusted Advisor
- Change management : Auto scaling, CloudWatch, CloudTrail, AWS Config
- Failure management : Backups, CloudFormation, S3, S3 Glacier, Route 53

### 4) Performance Efficiency
Includes the ability to use computing resources efficiently to meet system requirements, and to maintain that efficiency as demand changes and technologies evolve

#### Design Principles :
- Democratize advanced technologies - Advance technologies become services and hence you can focus more on product development
- Go global in minutes - Easy deployment in multiple regions
- Use serverless architectures - Avoid burden of managing servers
- Experiment more often - Easy to carry out comparative testing
- Mechanical sympathy - Be aware of all AWS services 

#### AWS services used fo performance efficiency :
- Selection : Auto Scaling, AWS Lambda, Amazon EBS, Amazon (S3), Amazon RDS
- Review : AWS CloudFormation, AWS News Blog
- Monitoring : Amazon CloudWatch, AWS Lambda
- Tradeoffs : Amazon RDS, Amazon ElastiCache, AWS Snowball, Amazon CloudFront

### 5) Cost Optimization
Includes the ability to run systems to deliver business value at the lowest price point

#### Design Principles :
- Adopt a consumption mode - Pay only for what you use
- Measure overall efficiency - Use CloudWatch
- Stop spending money on data center operations - AWS does the infrastructure part and enables customer to focus on organization projects
- Analyze and attribute expenditure - Accurate identification of system usage and costs, helps measure return on investment (ROI) - Make sure to use tags
- Use managed and application level services to reduce cost of ownership - As managed services operate at cloud scale, they can offer a lower cost per transaction or service

#### AWS services used for Cost Optimization :
- Expenditure Awareness : AWS Budgets, AWS Cost and Usage Report, AWS Cost Explorer, Reserved Instance Reporting
- Cost-Effective Resources : Spot instance, Reserved instance, Amazon S3 Glacier
- Matching supply and demand : AWS Auto Scaling, AWS Lambda
- Optimizing Over Time : AWS Trusted Advisor, AWS Cost and Usage Report,AWS News Blog

### 6) Sustainability
The sustainability pillar focuses on minimizing the environmental impacts of running cloud workloads.

#### Design Principles
- Understand your impact – establish performance indicators, evaluate improvements
- Establish sustainability goals – Set long-term goals for each workload, model return on investment (ROI)
- Maximize utilization – Right size each workload to maximize the energy efficiency of the underlying hardware and minimize idle resources.
- Anticipate and adopt new, more efficient hardware and software offerings – and design for flexibility to adopt new technologies over time.
- Use managed services – Shared services reduce the amount of infrastructure; Managed services help automate sustainability best practices as moving infrequent accessed data to cold storage and adjusting compute capacity.
- Reduce the downstream impact of your cloud workloads – Reduce the amount of energy or resources required to use your services and reduce the need for your customers to upgrade their devices 

#### AWS services used for Sustainability :
- EC2 Auto Scaling, Serverless Offering (Lambda, Fargate)
- Cost Explorer, AWS Graviton 2, EC2 T instances, @Spot Instances
- EFS-IA, Amazon S3 Glacier, EBS Cold HDD volumes
- S3 Lifecycle Configurations, S3 Intelligent Tiering
- Amazon Data Lifecycle Manager
- Read Local, Write Global: RDS Read Replicas, Aurora Global DB, DynamoDB Global Table, CloudFront


## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1630792886420926464)
