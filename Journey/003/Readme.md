
# AWS shared responsibility & Introduce to IAM : Course on Udemmy by Stepahane Mareek and aws academy Cloud Foundations [22444]

## Cloud Research
### Take Away Section 1: AWS shared responsibility model (aws academy : Module 4 - AWS Cloud Security) 
-  AWS and the customer share security responsibilities:

• AWS is responsible for security ofthe cloud

• Customer is responsible for security in the cloud
- AWS is responsible for protecting the infrastructure including hardware, software, networking, and facilities that run AWS Cloud services
- For services that are categorized as infrastructure as a service (IaaS), the customer is responsible for performing necessary security configuration and management tasks 

• For example, guest OS updates and security patches, firewall, security group configurations

### IAM - Identity and Access Management (Course on Udemmy - AWS Certified Cloud Practitioner Slides : slide 40)
- IAM is Global Service 
- root created by default and u shouldn't be used and shared 
- IAM = Identity and Access Management, Global service
- Users are people within your organization, and can be grouped
- Groups only contain users, not other groups
- Users don’t have to belong to a group, and user can belong to multiple groups

#### practice : create a user, create a group, enter the user into the group and test it.


### Permissions (Course on Udemmy - AWS Certified Cloud Practitioner Slides : slide 41)
- Users or Groups can be assigned JSON documents called policies
- These policies define the permissions of the users
- In AWS you apply the least privilege principle: don’t give more permissions than a user needs 

### IAM Policies (Course on Udemmy - AWS Certified Cloud Practitioner Slides : slide 43)
- Consists of version,id and statement
- statement contain of Sid,effect,principal,action,resource,and condition 

### Password Policy (Course on Udemmy - AWS Certified Cloud Practitioner Slides : slide 44)
- strong password 
- setup password policy : 

>  • Set a minimum password length
>
>  • Require specific character types
>
>  • Allow all IAM users to change their own passwords
>
>  • Require users to change their password after some time (password expiration)
>
>  • Prevent password re-use
 
### Take Away Section 2: AWS IAM (aws academy : Module 4 - AWS Cloud Security)

- IAM policies are constructed with JavaScript Object Notation (JSON) and define permissions.
- IAM policies can be attached to any IAM entity.
- Entities are IAM users, IAM groups, and IAM roles.
- An IAM user provides a way for a person, application, or service to authenticate to AWS.
- An IAM group is a simple way to attach the same policies to multiple users.
- An IAM role can have permissions policies attached to it and can be used to delegate temporary access to users or applications.

## Social Proof

✍️ Show that you shared your process on Twitter or LinkedIn

[twitter](https://mobile.twitter.com/tiaradwim1306/status/1611377077252689920)
