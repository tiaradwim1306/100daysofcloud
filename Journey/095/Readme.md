# Advanced Identity in AWS : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
### AWS Organizations
Global service, Allows to manage multiple AWS accounts. The main account is the management account and other accounts are member accounts. Member accounts can only be part of one organization.

Consolidated Billing (penagihan gabungan) across all accounts - single payment method. Pricing benefits from aggregated usage(penggunaan yg dikumpulkan) sehingga volume discount for EC2, S3, etc. Shared reserved instances and Savings Plans discounts across accounts. API is available to automate AWS account creation

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/dc6e5381-a7c9-4910-b96e-f655993bc1b4)

Advantages
- Multi Account vs One Account Multi VPC
- Use tagging standards for billing purposes
- Enable CloudTrail on all accounts, send logs to central S3 account
- Send CloudWatch Logs to central logging account
- Establish Cross Account Roles for Admin purposes

Security: Service Control Policies (SCP)
- IAM policies applied to OU or Accounts to restrict Users and Roles
- They do not apply to the management account (full admin power)
- Must have an explicit allow (does not allow anything by default – like IAM)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/885c8fa5-5dcb-4d3d-9364-e2549bfd7349)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/c73d7686-1089-4b25-a8d0-142351e6e9d7)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/c0ae07ae-96fc-44ea-adcc-d39c35b9f27d)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/ae75f98d-6a5a-41e1-b58f-aaf4bf3dc148)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/b3079aec-3d76-4eb7-9518-fafa44ac268a)

> aws:PrincipalOrgID can be used in any resource policies to restrict access to accounts that are member of an AWS Organization

#### IAM Roles vs Resource Based Policies
Cross account: 
- attaching a resource-based policy to a resource (example: S3 bucket policy) 
- OR using a role as a proxy

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/527e4e5f-2603-4de5-8e6f-4c6149978be2)

- When you assume a role (user, application or service), berarti kita melepas original permissions and take the permissions assigned to the role.
- When using a resource-based policy, principal tidak perlu melepas permissionnya.
example : User in account A needs to scan a DynamoDB table in Accoun and dump it in an S3 bucket in Account B.

> Supported : Amazon S3 buckets, SNS topics, SQS queues, etc…

### Amazon EventBridge – Security
- when a rule runs, it needs permissions on the target
- resource-based policy: Lambda, SNS, SQS, CloudWatch Logs, API Gateway…
- IAM role: Kinesis stream, Systems Manager Run Command, ECS task…

#### IAM Permission Boundaries
- IAM Permission Boundaries are supported for users and roles (not groups) 
- Advanced feature to use a managed policy to set the maximum permissions yang diperoleh IAM entity.

> Can be used in combinations of AWS Organizations SCP

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/41206130-56ff-4ae6-89df-5bd3949bb12d)

- Delegate responsibilities to non administrators sesuai batas izin mereka, for example create new IAM users.
- Allow developers to self-assign policies and manage their own permissions, while making sure they can’t “escalate” (meningkatkan) privileges (= make themselves admin).
- Useful to restrict one specific user (instead of a whole account using Organizations & SCP)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/37bcd1a8-a090-4da5-add1-c859f0aa26c4)

kita tidak bisa CreateQueue karena jelas dipermission tersebut effect nya deny, lalu apakah kita bisa DeleteQueue walaupun disini kita mempunyai explicit rule yang menyatakan DeleteQueue adalah Allow namun yang dibaca oleh rule adalah yg paling atas sehingga disini kita juga tidak bisa melakukan DeleteQueue.
Terus apakah kita bisa DescribeInstance? tentu saja tidak bisa karena dia tidak ada di rule tersebut. 

### AWS IAM Identity Center
one login (single sign-on → SSO) for all you : 
- AWS accounts in AWS Organizations
- Business cloud applications (e.g., Salesforce, Box, Microsoft 365, …)
- SAML2.0-enabled applications
- EC2 Windows Instances

> identity providers : build identity store di IAM identity center, 3rd party: Active Directory (AD), OneLogin, Okta

#### Fine-grained Permissions and Assignments (Izin dan penugasan yg sangat rinci)
Multi-Account Permissions : 
- bisa memanage beberapa akun di AWS organization
- Permission Sets : kumpulan dari beberapa IAM Policies yg assigned ke users dan groups untuk define aws access.

Application Assignments : 
- SSO access to many SAML 2.0 business applications (Salesforce, Box, Microsoft 365, ...)
- Provide required URLs, certificates, and metadata

Attribute-Based Access Control (ABAC)
- Fine-grained permissions(izin terperinci) based on users’ attributes stored in IAM Identity Center Identity Store
- Example: cost center, title, locale, ...
- Use case: Define permissions once, then modify AWS access by changing the attributes

### Microsoft AD (Active Directory)
- AD adalah software yang ditemukan di Windows Server manapun dengan AD Domain Services, 
- Database object, yg object nya bisa berupa Computers, Printers, File Shares, Security Groups.
- Centralized security management : digunakan untuk create account and assign permissions, etc.
- semua objects akan diatur kedalam trees, dan kumpulan trees disebut forest

### AWS Directory Services
- AWS Managed Microsoft AD : create AD sendiri di AWS, manage users locally and support MFA. membangun trust connection di on-promises AD
- AD Connecter : Directory gateway (proxy) untuk redirect ke AD lokal, support MFA. users dimanage di AD local
- Simple AD : AD-compatible manage directory di AWS, tidak bisa digabungkan dengan AD local

### Active Directory Setup
- Connect to an AWS Managed Microsoft AD (Directory Service) : Integration is out of the box
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/31ab3dbf-e359-4417-8ccc-94b202d8f028)

- Connect to a Self-Managed Directory : Create Two-way Trust Relationship using AWS Managed Microsoft AD and Create an AD Connector
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/cac30f56-9038-4d4a-aecd-577d9d1be723)

### AWS Control Tower
Easy way to set up and govern (mengatur) a secure and compliant multi-account AWS environment based on best practices, WS Control Tower uses AWS Organizations to create accounts

Benefits : 
- Automate the set up of your environment in a few clicks
- Automate ongoing policy management using guardrails
- Detect policy violations (pelanggaran) and remediate (memperbaiki) them
- Monitor compliance through an interactive dashboard

Guardrails
- Provides ongoing governance (tata kelola berkelanjutan)  for your Control Tower environment (AWS Accounts)
- Preventive (pencegahan) Guardrail – using SCPs (e.g., Restrict Regions across all your accounts)
- Detective Guardrail – using AWS Config (e.g., identify untagged resources)

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1750883856029274495)




