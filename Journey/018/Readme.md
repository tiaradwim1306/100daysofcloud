
# Cloud Monitoring : Course on Udemmy by Stepahane Mareek

## Cloud Research
### Amazon CloudWatch Metrics
- CloudWatch provides metrics for every service in AWS
- Metric is a variable to monitor (CPU Utilization, NetworkIn…)
- Metrics have timestamps
- Can create CloudWatch dashboards of metrics

example: 
CloudWatch metrics such as Billing metrics, which are only available in us-east-I. This metric represents the total amounts you have spent on your AWS cloud.
It will be updated monthly

Important Metrics
- EC2 instances: CPU Utilization, Status Checks, Network (not RAM)
	- Default metrics every 5 minutes
	- Option for Detailed Monitoring ($$$): metrics every 1 minute
- EBS volumes: Disk Read/Writes
- S3 buckets: BucketSizeBytes, NumberOfObjects, AllRequests
- Billing:Total Estimated Charge (only in us-east-1)
- Service Limits: how much you've been using a service API
- Custom metrics: push your own metrics

### Amazon CloudWatch Alarms
- Alarms are used to trigger notifications for any metric
- Alarms actions…
	- Auto Scaling: increase or decrease EC2 instances “desired” count
	- EC2 Actions: stop, terminate, reboot or recover an EC2 instance
	- SNS notifications: send a notification into an SNS topic
- Various options (sampling, %, max, min, etc…)
- Can choose the period on which to evaluate an alarm
- Example: create a billing alarm on the CloudWatch Billing metric

### Amazon CloudWatch Logs 
- CloudWatch Logs can collect log from Elastic Beanstalk, ECS, AWS Lambda, CloudTrail, CloudWatch, Route53 
- Enables real-time monitoring of logs and adjustable CloudWatch Logs retention

CloudWatch Logs for EC2
- By default, no logs from your EC2 instance will go to CloudWatch
- You need to run a CloudWatch agent on EC2 to push the log files you want
- Make sure IAM permissions are correct
- The CloudWatch log agent can be setup on-premises too

### Amazon EventBridge
- Schedule -> Cron jobs (scheduled scripts) 
- Event Pattern -> : Event rules to react to a service doing something 
- Trigger Lambda functions, send SQS/SNS messages…
- Schema Registry: model event schema
- You can archive events (all/filter) sent to an event bus (indefinitely or set period)
- Ability to replay archived events

### CloudTrail
- Provides governance, compliance and audit for your AWS Account
- CloudTrail is enabled by default!
- Get an history of events / API calls made within your AWS Account by: Console, SDK, CLI, AWS Services
- Can put logs from CloudTrail into CloudWatch Logs or S3
- A trail can be applied to All Regions (default) or a single Region.

example : If a resource is deleted in AWS, investigate CloudTrail first!

### X-Ray
we need debugging in production but no general view of the whole architecture,X-Ray can fix it!!!
X-ray is visual analysis of our application

advantages :
- Troubleshooting performance (bottlenecks) 
- Understand dependencies in a microservice architecture 
- Pinpoint service issues 
- Review request behavior 
- Find errors and exceptions 
- Are we meeting time SLA? 
- Where I am throttled? 
- Identify users that are impacted 

### CodeGuru
-  An ML-powered service for automated code reviews and application performance recommendations
- Provides two functionalities
	- CodeGuru Reviewer: automated code reviews for static code analysis (development)
	- CodeGuru Profiler: visibility/recommendations about application performance during runtime (production)

Amazon CodeGuru Reviewer
- Identify critical issues, security vulnerabilities, and hard-to-find bugs
- Uses Machine Learning and automated reasoning
- Supports Java and Python
- Integrates with GitHub, Bitbucket, and AWS CodeCommit

Example: common coding best practices,resource leaks, security detection, input validation

Amazon CodeGuru Profiler
- Helps understand the runtime behavior of your application
- Features:
- Identify and remove code inefficiencies
- Improve application performance (e.g., reduce CPU utilization)
- Decrease compute costs
- Provides heap summary (identify which objects using up memory)
- Anomaly Detection
- Support applications running on AWS or on- premise
- Minimal overhead on application

Example: identify if your application is consuming excessive CPU capacity on a logging routine

### AWS Health Dashboard 
- Shows all regions, all services health
- Shows historical information for each day
- Has an RSS feed you can subscribe to

## Summary
- CloudWatch:
	- Metrics: monitor the performance of AWS services and billing metrics
	- Alarms: automate notification, perform EC2 action, notify to SNS based on metric
	- Logs: collect log files from EC2 instances, servers, Lambda functions…
	- Events (or EventBridge): react to events in AWS, or trigger a rule on a schedule
- CloudTrail: audit API calls made within your AWS account
- CloudTrail Insights: automated analysis of your CloudTrail Events
- X-Ray: trace requests made through your distributed applications
- Service Health Dashboard: status of all AWS services across all regions
- Personal Health Dashboard: AWS events that impact your infrastructure
- Amazon CodeGuru: automated code reviews and application performance recommendations

## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1618507587254906881)
