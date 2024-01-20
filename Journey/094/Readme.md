# AWS Monitoring, Audit and Performance : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
### Amazon CloudWatch Metrics
Cloudwatch menyediakan metric untuk setiap service di AWS, Metric adalah variable untuk monitor (CPU Utilization,Networking,...).Metrics memiliki namespace.
Dimension adalah atribut dari metric  (instance id, environment, etc…).up to 30 dimensions per metric. Can create cloudwatch dashboard of metric dan bisa membuat CloudWatch custom metrics.

#### CloudWatch Metric Streams
stream metric cloudwatch secara terus-menerus ketujuan yang anda pilih dengan near-real-time delivery and low latency.
opsi filter metrics yang digunakan agar hanya sebagian metric saja yg dihasilkan

#### CloudWatch Logs
Log groups : arbitrary name, mewakili suatu aplikasi
Log stream : file log dari aplikasi/ log files / containers
kita dapat mendefinisikan log expiration policies, example : never expire, 1 day to 10 years.
Cloudwatch logs can send logs to : S3, Kinesis Data Stream, Kinesis Data Firehouse, AWS Lambda, OpenSearch.
Log ter encrypted by default namun juga bisa menggunakan KMS-based encryption dengan keys mu sendiri.

Apa saja yg bisa menggunakan Cloudwatch log : 
- SDK, CloudWatch Logs Agent, CloudWatch Unified Agent
- Elastic Beanstalk: collection of logs from application
- ECS: collection from containers
- AWS Lambda: collection from function logs
- VPC Flow Logs: VPC specific logs
- API Gateway
- CloudTrail based on filters
- Route53: Log DNS queries

#### CloudWatch Logs Insights
digunakan untuk mencari dan menganalisis data log yg disimpan. example : mencari IP tertentu dalam log,mencari ‘ERROR’ di log. Bisa query multiple Log groups di AWS akun yg berbeda.It’s a query engine, not a real-time engine. menyediakan query language yang dibuat khusus : 
- Secara otomatis menemukan bagian dari service AWS dan JSON log event
- Ambil bidang acara yang diinginkan, filter berdasarkan kondisi, hitung statistik agregat, urutkan acara, batasi jumlah acara…
- Dapat menyimpan kueri dan menambahkannya ke Dasbor CloudWatch

#### CloudWatch Logs – S3 Export
Log data can take up to 12 hours to become available for export, The API call is CreateExportTask, Not near-real time or real-time.use Logs Subscriptions instead

#### CloudWatch Logs Subscriptions
Get a real-time log events from CloudWatch Logs for processing and analysis, Send to Kinesis Data Streams, Kinesis Data Firehose, or Lambda.
Subscription Filter – filter which logs are events delivered to your destination

Cross-Account Subscription – send log events to resources in a different AWS account (KDS, KDF)

#### Cloudwatch Logs for EC2
by default, no logs from EC2 go to Cloudwatch, kita butuh run CloudWatch agent agar EC2 push log files ke Cloudwatch.Dengan syarat berikan IAM permission yang benar.
> The CloudWatch log agent can be setup on-premises too

CloudWatch Logs Agent
- Old version of the agent
- Can only send to CloudWatch Logs

CloudWatch Unified Agent
- Collect additional system-level metrics such as RAM, processes, etc…
- Collect logs to send to CloudWatch Logs
- Centralized configuration using SSM Parameter Store

CloudWatch Unified Agent – Metrics
- Collected directly on your Linux server / EC2 instance
- CPU (active, guest, idle, system, user, steal)
- Disk metrics (free, used, total), Disk IO (writes, reads, bytes, iops)
- RAM (free, inactive, used, total, cached)
- Netstat (number of TCP and UDP connections, net packets, bytes)
- Processes (total, dead, blocked, idle, running, sleeping)
- Swap Space (free, used, used %)
- Reminder: out-of-the box metrics for EC2 – disk, CPU, network (high level)

#### CloudWatch Alarms
Alarms are used to trigger notifications for any metric, Various options (sampling, %, max, min, etc…). 

Alarm States:
- OK
- INSUFFICIENT_DATA
- ALARM

Period:
- Length of time in seconds to evaluate the metric
- High resolution custom metrics: 10 sec, 30 sec or multiples of 60 sec

CloudWatch Alarm Targets 
- Stop, Terminate, Reboot, or Recover an EC2 Instance 
- Trigger Auto Scaling Action 
- Send notification to SNS (from which you can do pretty much anything)

CloudWatch Alarms – Composite Alarms
Alarm CloudWatch menggunakan satu metrik, Composite Alarm memantau status beberapa alarm lainnya.mempunyai 2 conditions AND and OR. Helpful to reduce “alarm noise” by creating complex composite alarms

CloudWatch Alarm: good to know : 
- Alarms can be created based on CloudWatch Logs Metrics Filters
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/81f85ff1-e3b0-41ab-b07d-bedf15c5749e)

- To test alarms and notifications, set the alarm state to Alarm using CLI
> aws cloudwatch set-alarm-state --alarm-name "myalarm" --state-value ALARM --state-reason "testing purposes"

#### CloudWatch EventBridge
- Schedule: Cron jobs (scheduled scripts)
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/6c2abdbb-a01d-4cc9-9a73-2a6a85f526af)

- Event Pattern: Event rules to react to a service doing something 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/8be0e476-10dc-4148-8d6f-14872078d3e4)

- Trigger Lambda functions, send SQS/SNS messages…

Event buses can be accessed by other AWS accounts using Resource-based Policies, can archive events (all/filter) sent to an event bus (indefinitely or set period), Ability to replay archived events.

#### Amazon EventBridge – Schema Registry 
EventBridge can analyze the events in your bus and infer the schema. The Schema Registry allows you to generate code for your application, that will know in advance how data is structured in the event bus, Schema can be versioned.

#### Amazon EventBridge – Resource-based Policy 
Manage permissions for a specific Event Bus, for example: allow/deny events from another AWS account or AWS region 
> Use case: aggregate all events from your AWS Organization in a single AWS account or AWS region

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/260df0c6-457f-4e1c-8439-d167ee046d14)

#### CloudWatch Container Insights
- Mengumpulkan, menggabungkan, meringkas metrik dan log dari kontainer.Tersedia untuk ECS, RKS, Kubernetes platform on EC2, Fargate.
> In Amazon EKS and Kubernetes, CloudWatch Insights is using a containerized version of the CloudWatch Agent to discover containers.

#### CloudWatch Lambda Insights
- Monitoring and troubleshooting solution for serverless applications running on AWS Lambda.
- Collects, aggregates, and summarizes system-level metrics including CPU time, memory, disk, and network.
- Collects, aggregates, and summarizes diagnostic information such as cold starts and Lambda worker shutdowns.
- Lambda Insights is provided as a Lambda Layers.

#### CloudWatch Contributor Insights 
- Analyze log data and create time series that display contributor data. 
- See metrics about the top-N contributors 
- The total number of unique contributors, and their usage. 
- This helps you find top talkers and understand who or what is impacting system performance. 
- Works for any AWS-generated logs (VPC, DNS, etc..) 
- For example, you can find bad hosts, identify pengguna jaringan terberat, or find the URLs yang menghasilkan kesalahan terbanyak.
- You can build your rules from scratch, or you can also use sample rules that AWS has created – memanfaatkan CloudWatch Logs 
- CloudWatch also provides built-in rules that you can use to analyze metrics from other AWS services.

#### CloudWatch Application Insights 
- Provides automated dashboards that show potential problems with monitored applications, to help isolate ongoing issues 
- Your applications run on Amazon EC2 Instances with select technologies only (Java, .NET, Microsoft IIS Web Server, databases…)
- And you can use other AWS resources such as Amazon EBS, RDS, ELB, ASG, Lambda, SQS, DynamoDB, S3 bucket, ECS, EKS, SNS, API Gateway… 
- Powered by SageMaker 
- Peningkatan visibility into your application health to reduce the time it will take you to troubleshoot and repair your applications 
- Findings and alerts are sent to Amazon EventBridge and SSM OpsCenter

#### CloudWatch Insights and Operational Visibility 
- CloudWatch Container Insights :  ECS, EKS, Kubernetes on EC2, Fargate, needs agent for Kubernetes. Metrics and logs 
- CloudWatch Lambda Insights : Detailed metrics to troubleshoot serverless applications 
- CloudWatch Contributors Insights : Find “Top-N” Contributors through CloudWatch Logs 
- CloudWatch Application Insights : Automatic dashboard to troubleshoot your application and related AWS services 

### AWS CloudTrail
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/f11fc312-62fb-4abb-97cb-0fa3dfff5cd4)

provide governance (tata kelola), compliance (kepatuhan), and audit ke AWS akun, CloudTrail enabled by default.
Get an history of events / API calls made within your AWS Account by Console, SDK, CLI, AWS Service. Can put logs from CloudTrail into CloudWatch Logs or S3.

A trail can be applied to All Regions (default) or a single Region, If a resource is deleted in AWS, investigate CloudTrail first!

#### CloudTrail Events 
- Management Events: 
Operations that are performed on resources in your AWS account, Examples: 
  - Configuring security (IAM AttachRolePolicy) 
  - Configuring rules for routing data (Amazon EC2 CreateSubnet) 
  - Setting up logging (AWS CloudTrail CreateTrail) 
By default, trails are configured to log management events, Can separate Read Events (that don’t modify resources) from Write Events (that may modify resources) 

- Data Events: 
By default, data events are not logged (because high volume operations), Amazon S3 object-level activity (ex: GetObject, DeleteObject, PutObject): can separate Read and Write Events. AWS Lambda function execution activity (the Invoke API)

#### CloudTrail Insights
Enable CloudTrail Insights to detect unusual activity in your account: 
- inaccurate resource provisioning 
- hitting service limits 
- Bursts of AWS IAM actions 
- Gaps in periodic maintenance activity 

CloudTrail Insights analyzes normal management events to create a baseline And then continuously analyzes write events to detect unusual patterns (pola yang tidak bisa). 
- Anomalies appear in the CloudTrail console 
- Event is sent to Amazon S3 
- An EventBridge event is generated (for automation needs)

CloudTrail Events Retention
Events are stored for 90 days in CloudTrail, to keep events beyond this period, log them to S3 and use Athena.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/f1f76f68-4c72-4b62-9216-aea0fffc05a3)

### AWS Config
Helps with auditing and recording compliance(kepatuhan) of your AWS resources, Helps record configurations and changes over time. Questions that can be solved by AWS Config :
- Is there unrestricted (tidak dibatasi) SSH access to my security groups?
- Do my buckets have any public access?
- How has my ALB configuration changed over time?

You can receive alerts (SNS notifications) for any changes, AWS Config is a per-region service, bisa menggabungkan data across regions and accounts. Memungkinkan store configuration data ke S3 and analyzed by Athena.


#### Config Rules
Can use AWS managed config rules (over 75), Can make custom config rules (must be defined in AWS Lambda), example : evaluate if each EBS disk is of type gp2 or evaluate if each EC2 instance is t2.micro.
Rules can be evaluated / triggered : For each config change and/or regular time intervals (secara berkala)

> Pricing: no free tier, $0.003 per configuration item recorded per region, $0.001 per config rule evaluation per region

Resource : 
- View compliance of a resource over time. example : misal ada security group yang telah melanggar rule yang sudah dibuat.
- View configuration of a resource over time. example : anda bisa melihat perubahan konfigurasi kapan dan siapa yang merubah dan sebagainya.
- View CloudTrail API calls of a resource over time, ditautkan ke cloudtrail agar mendapat gambaran.

Remediations 
- Automate remediation of non-compliant(tidak patuh) resources using SSM Automation Documents 
- Use AWS-Managed Automation Documents or create custom Automation Documents, Tip: you can create custom Automation Documents that invokes Lambda function 
- You can set Remediation Retries if the resource is still non-compliant after auto- remediation

Notifications 
- Use EventBridge to trigger notifications when AWS resources are noncompliant 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/13c4ebdd-1eca-4140-9474-82111ea4c840)

- Ability to send configuration changes and compliance state notifications to SNS (all events-use SNS Filtering or filter at client-side)
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/ed908416-aede-434f-865e-b31bc963272a)

## Summary
CloudWatch vs CloudTrail vs Config 
- CloudWatch : Performance monitoring (metrics, CPU, network, etc…) & dashboards, events & Alerting, Log Aggregation & Analysis.
- CloudTrail : Record API calls made within your Account by everyone, Can define trails for specific resources, Global Service.
- Config : Record configuration changes, Evaluate resources against compliance rules, Get timeline of changes and compliance.

For an Elastic Load Balancer 
- CloudWatch :  Monitoring Incoming connections metric, Visualize error codes as % over time, Make a dashboard to get an idea of your load balancer performance.
- Config : Track security group rules for the Load Balancer, Track configuration changes for the Load Balancer, Ensure an SSL certificate is always assigned to the Load Balancer (compliance).
CloudTrail : Track who made any changes to the Load Balancer with API calls.

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1748553678825623833)





