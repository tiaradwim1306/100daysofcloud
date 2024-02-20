# Other Services : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
### CloudFormation
CloudFormation is a declarative way of outlining your AWS Infrastructure, for any resources (most of them are supported). Example : create CloudFormation template untuk membuat security group, EC2 instances, S3 bucket, etc.
> Then CloudFormation creates those for you, in the right order, with the exact configuration that you specify.

### Benefit : 
- infrastructure as code : No resources are manually created, which is excellent for control. Changes to the infrastructure are reviewed through code.
- cost : Each resources within the stack is tagged with an identifier so you can easily see how much a stack costs you, You can estimate the costs of your resources using the CloudFormation template. Savings strategy: In Dev, you could automation deletion of templates at 5 PM and recreated at 8 AM, safely
- Productivity : Ability to destroy and re-create an infrastructure on the cloud on the fly, Automated generation of Diagram for your templates. Declarative programming (no need to figure out ordering and orchestration).
- Don’t re-invent the wheel : Leverage existing templates on the web and Leverage the documentation.
- Supports (almost) all AWS resources : Everything we’ll see in this course is supported, You can use “custom resources” for resources that are not supported.

### CloudFormation Stack Designer
Example: WordPress CloudFormation Stack, We can see all the resources and see the relations between the components

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/cbfc33c7-ae3c-4f9b-bcb9-55b3d55a2162)

### Amazon Simple Email Service (Amazon SES)
- Fully managed service to send emails securely, globally and at scale
- Allows inbound/outbound emails
- Reputation dashboard, performance insights, anti-spam feedback
- Provides statistics such as email deliveries, bounces, feedback loop results, email open
- Supports DomainKeys Identified Mail (DKIM) and Sender Policy Framework (SPF)
- Flexible IP deployment: shared, dedicated, and customer-owned IPs
- Send emails using your application using AWS Console, APIs, or SMTP
> Use cases: transactional, marketing and bulk email communications

### Amazon Pinpoint
- Scalable 2-way (outbound/inbound) marketing communications service
- Supports email, SMS, push, voice, and in-app messaging
- Ability to segment and personalize messages with the right content to customers
- Possibility to receive replies
- Scales to billions of messages per day
> Use cases: run campaigns by sending marketing, bulk, transactional SMS messages

### Amazon SNS or Amazon SES
- In SNS & SES you managed each message's audience, content, and delivery schedule 
- In Amazon Pinpoint, you create message templates, delivery schedules, highly-targeted segments, and full campaigns

### Systems Manager 
SSM Session Manager : 
allows you to start a secure shell on your EC2 and on-premises servers. Supports Linux, macOS, and Windows. Send session log data to S3 or CloudWatch Logs.
> No SSH access, bastion hosts, or SSH keys needed and No port 22 needed (better security)

#### Run Command : 
Execute a document (= script) or just run a command, Run command across multiple instances (using resource groups). No need for SSH.
Command Output can be shown in the AWS Console, sent to S3 bucket or CloudWatch Logs. Send notifications to SNS about command status (In progress, Success, Failed, …).
> Integrated with IAM & CloudTrail and can be invoked using EventBridge

#### Patch Manager : 
Automates the process of patching managed instances. yaitu OS updates, applications updates, security updates. Supports EC2 instances and on-premises servers. Patch on-demand or on a schedule using Maintenance Windows. Scan instances and generate patch compliance report (missing patches).
> Supports Linux, macOS, and Windows

#### Maintenance Windows : 
Defines a schedule for when to perform actions on your instances, Example: OS patching, updating drivers, installing software, etc. Maintenance Window contains : Schedule, Duration, Set of registered instances, Set of registered tasks.

#### Automation : 
Simplifies common maintenance and deployment tasks of EC2 instances and other AWS resources, Examples: restart instances, create an AMI, EBS snapshot.
> Automation Runbook :  SSM Documents to define actions preformed on your EC2 instances or AWS resources (pre-defined or custom). Can be triggered using :
- Manually using AWS Console, AWS CLI or SDK
- Amazon EventBridge
- On a schedule using Maintenance Windows
- By AWS Config for rules remediation

### Cost Explorer
Visualize, understand, and manage your AWS costs and usage over time. Create custom reports that analyze cost and usage data. Analyze your data at a high level: total costs and usage across all accounts. Or Monthly, hourly, resource level granularity. Choose an optimal Savings Plan (to lower prices on your bill).
> Forecast usage up to 12 months based on previous usage

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/d81d2c39-069e-4e56-aeff-789d1e65fd07)

### AWS Batch
fully managed batch processing pada skala apapun, run 100,000s of computing batch jobs on AWS secara efisien.
A “batch” job is a job with a start and an end (kebalikan dari pekerjaan berkelanjutan), Batch will dynamically launch EC2 instances or Spot Instances and provides the right amount of compute / memory. Anda mengirimkan atau schedule batch jobs and AWS Batch akan melakukan sisanya. Helpful for cost optimizations and mengurangi fokus pada infrastructure.
> Batch jobs are defined as Docker images and run on ECS

### Batch vs Lambda 
Lambda : 
- Time limit 
- Limited runtimes 
- Limited temporary disk space 
- Serverless

Batch :
- No time limit 
- Any runtime as long as it’s packaged as a Docker image 
- Berdasarkan EBS / instance store for disk space 
- Didasari EC2 (can be managed by AWS)

### Amazon AppFlow
Fully managed integration service that enables you to securely transfer data between Software-as-a-Service (SaaS) applications and AWS.
- Sources: Salesforce, SAP, Zendesk, Slack, and ServiceNow
- Destinations: AWS services like Amazon S3, Amazon Redshift or nonAWS such as SnowFlake and Salesforce
- Frequency: on a schedule, in response to events, or on demand
- Kemampuan Data transformation like filtering and validation
- Encrypted over the public internet or privately over AWS PrivateLink
> Don't spend time for writing integrations and take advantage of the API right away.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/4a554859-e1de-4d44-b565-4c176f9b4d79)

### AWS Amplify
A set of tools and services that helps you develop and deploy scalable full stack web and mobile applications.Authentication, Storage, API (REST, GraphQL), CI/CD, PubSub, Analytics, AI/ML Predictions, Monitoring, etc.
Connect your source code from GitHub, AWS CodeCommit, Bitbucket, GitLab, or upload directly.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/74a075ad-cff5-42a9-a7b3-529178cc9703)

## Exam Review & Tips
exam guide : https://aws.amazon.com/certification/certified-solutions-architect-associate/ 

Links to Whitepapers : 
1. Architecting for the cloud: https://d1.awsstatic.com/whitepapers/AWS_Cloud_Best_Practices.pdf (Archived)
2. Whitepapers related to well-architected framework are mentioned here: https://aws.amazon.com/blogs/aws/aws-well-architected-framework-updated-white-papers-tools-and-best-practices/
3. Disaster recovery whitepaper: https://d1.awsstatic.com/whitepapers/aws-disaster-recovery.pdf (Archived)
AWS now recommends a well-architected framework whitepaper: https://d1.awsstatic.com/whitepapers/architecture/AWS_Well-Architected_Framework.pdf

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1759852180633473209)

