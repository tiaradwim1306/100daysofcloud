
# IAM PART 2 : Course on Udemmy by Stepahane Mareek and aws academy Cloud Foundations [22444]

## Cloud Research
security is very important for root, because administrators have access to change configurations and even delete resources in your AWS account, for this you need more secure security.

### Securing a new AWS account : Take Away Section 3: Securing a new AWS account (aws academy : Module 4 - AWS Cloud Security)

Best practices to secure an AWS account :
- Secure logins with multi-factor authentication (MFA).
- Delete account root user access keys.
- Create individual IAM users and grant permissions according to the principle of least privilege.
- Use groups to assign permissions to IAM users.
- Configure a strong password policy.
- Delegate using roles instead of sharing credentials.
- Monitor account activity by using AWS CloudTrail.

## MFA - Multi Factor Authentication
security is very important for root, because administrators have access to change configurations and even delete resources in your AWS account, for this you need more secure security like MFA
- the main benefit is that if the password is stolen or hacked, the account will not be compromised.
- security that applies not only to the root user but also to all IAM users

### MFA Device
some of the MFA devices that we can find on AWS are:
1. virtual MFA device 
- Google Authenticator (phone only)
- Authy (multi-device)
2. Universal 2nd Factor (U2F) Security Key
- YubiKey by Yubico (3rd party)
3. Hardware Key Fob MFA Device
- Provided by Gemalto (3rd party)
4. Hardware Key Fob MFA Device for AWS GovCloud (US)
- Provided by SurePassID (3rd party)

### How can users access AWS ? 
1. AWS Management Console - Easy-to-use graphical interface
2. Command Line Interface (AWS CLI) - Access to services by discrete commands or scripts
3. Software Development Kits (SDKs) - Access services directly from your code (such as Java, Python, and others)

### IAM Roles For Service 
policies for services

### IAM Security Tools
- IAM Credentials Report (account-level)
report security information for each user such as when it was created, password, MFA is active or not, and so on
- IAM Access Advisor (user-level)
displays the service permission granted to the user and when it was last accessed

## Social Proof

[Twitter](https://mobile.twitter.com/tiaradwim1306/status/1611598133456433153)
