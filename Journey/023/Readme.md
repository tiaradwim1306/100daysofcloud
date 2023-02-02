
# Security & Compliance Part 3 : Course on Udemmy by Stepahane Mareek

## Cloud Research

### AWS Security Hub
- Central security tool to manage security across several AWS accounts and automate security checks
- Integrated dashboards showing current security and compliance status to quickly take actions
- Automatically aggregates alerts in predefined or personal findings formats from various AWS services & AWS partner tools

### Amazon Detective
- Sometimes security findings require deeper analysis to isolate the root cause and take action – it’s a complex process
- Amazon Detective analyzes, investigates, and quickly identifies the root cause of security issues or suspicious activities (using ML and graphs)
- Automatically collects and processes events from VPC Flow Logs,CloudTrail, GuardDuty and create a unified view
- Produces visualizations with details and context to get to the root cause

### AWS Abuse
- Report suspected AWS resources used for abusive or illegal purposes
- Abusive & prohibited behaviors are:
	- Spam – receving undesired emails from AWS-owned IP address, websites & forums spammed by AWS resources
	- Port scanning – sending packets to your ports to discover the unsecured ones
	- DoS or DDoS attacks – AWS-owned IP addresses attempting to overwhlem or crash your servers/softwares
	- Intrusion attempts – logging in on your resources
	- Hosting objectionable or copyrighted content – distributing illegal or copyrighted content without consent
	- Distributing malware – AWS resources distributing softwares to harm computers or machines
- Contact the AWS Abuse team: AWS abuse form, or abuse@amazonaws.com

### Root user privileges
- Root user = Account Owner (created when the account is created)
- Has complete access to all AWS services and resources
- Lock away your AWS account root user access keys!
- Do not use the root account for everyday tasks, even administrative tasks
- Actions that can be performed only by the root user:
	- Change account settings (account name, email address, root user password, root user access keys)
	- View certain tax invoices
	- Close your AWS account
	- Restore IAM user permissions
	- Change or cancel your AWS Support plan
	- Register as a seller in the Reserved Instance Marketplace
	- Configure an Amazon S3 bucket to enable MFA
	- Edit or delete an Amazon S3 bucket policy that includes an invalid VPC ID or VPC endpoint ID
	- Sign up for GovCloud

## SUMMARY 
- Shared Responsibility on AWS
- Shield: Automatic DDoS Protection + 24/7 support for advanced
- WAF: Firewall to filter incoming requests based on rules
- KMS: Encryption keys managed by AWS
- CloudHSM: Hardware encryption, we manage encryption keys
- AWS Certificate Manager: provision, manage, and deploy SSL/TLS Certificates
- Artifact: Get access to compliance reports such as PCI, ISO, etc…
- GuardDuty: Find malicious behavior with VPC, DNS & CloudTrail Logs
- Inspector: For EC2 only, install agent and find vulnerabilities
- Config: Track config changes and compliance against rules
- Macie: Find sensitive data (ex: PII data) in Amazon S3 buckets
- CloudTrail: Track API calls made by users within account
- AWS Security Hub: gather security findings from multiple AWS accounts
- Amazon Detective: find the root cause of security issues or suspicious activities
- AWS Abuse: Report AWS resources used for abusive or illegal purposes
- Root user privileges:
	- Change account settings
	- Close your AWS account
	- Change or cancel your AWS Support plan
	- Register as a seller in the Reserved Instance Marketplace



## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1621072162571550728)
