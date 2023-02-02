
# Security & Compliance Part 2 : Course on Udemmy by Stepahane Mareek

## Cloud Research

### AWS Secrets manager 
new service used to store secrets and can force the secret to be created with a lambda every X days.
integrated with amazon RDS and encrypted with KMS

### Artifact 
not service but portal that provides customers with on-demand access to AWS compliance documentation and AWS agreements

### Amazon GuardDuty
Service that helps perform intelligent threat discovery to protect your account.how to do it :
- Uses Machine Learning algorithms, anomaly detection, 3rd party data
- One click to enable (30 days trial), no need to install software
- Can protect against CryptoCurrency attacks (has a dedicated “finding” for it)
- Can setup CloudWatch Event rules to be notified in case of findings,can target AWS Lambda or SNS

### Amazon Inspector 
service that is used to run automatic security, for example:
- EC2 instances, utilizing SSM to Analyze accidental network accessibility and Analyze running OS
- Container Images push to Amazon ECR, assessment of Container Images as they are pushed
- Lambda function, Identifying software vulnerabilities and assessing the function when deployed
- Reporting & integration with AWS Security Hub
- Send findings to Amazon Event Bridge

### AWS Config
service that functions to audit and record AWS resource compliance by recording configurations and changes overtime, and the data is stored in S3 (analyzed by Athena).
- Notification of every change via SNS
- per-region services but can be combined across regions and accounts

### Amazon Macie 
- Amazon Macie is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover and protect your sensitive data in AWS.
- Macie helps identify and alert you to sensitive data, such as personally identifiable information (PII)


## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1621071000883564546)
