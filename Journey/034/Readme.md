
# AWS Directory Services & AWS IAM Identity Center : Course on Udemmy by Stepahane Mareek


## Cloud Research
### What is Microsoft Active Directory (AD)?
- Found on any Windows Server with AD Domain Services
- Database of objects: User Accounts, Computers, Printers, File Shares, Security Groups
- Centralized security management, create account, assign permissions

### AWS Directory Services
- AWS Managed Microsoft AD
	- Create your own AD in AWS, manage users locally, supports MFA
	- Establish “trust” connections with your on- premise AD
- AD Connector
	- Directory Gateway (proxy) to redirect to on- premise AD, supports MFA
	- Users are managed on the on-premise AD
- Simple AD
	- AD-compatible managed directory on AWS
	- Cannot be joined with on-premise AD


### AWS IAM Identity Center (successor to AWS Single Sign-On)
One login (single sign-on) for all your :
- AWS accounts in AWS Organizations
- Business cloud applications (e.g., Salesforce, Box, Microsoft 365, …)- SAML2.0-enabled applications
- EC2 Windows Instances

Identity providers :
- Built-in identity store in IAM Identity Center
-  3rd party: Active Directory (AD), OneLogin, Okta…

### Summary
- IAM : Identity and Access Management inside your AWS account and for users that you trust and belong to your company
- Organizations : manage multiple AWS accounts
- Security Token Service (STS) : temporary, limited-privileges credentials to access AWS resources
- Cognito : create a database of users for your mobile & web applications
- Directory Services : integrate Microsoft Active Directory in AWS
- IAM Identity Center : one login for multiple AWS accounts & applications


## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1626379542792372224)
