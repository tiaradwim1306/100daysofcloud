# AWS Security & Encryption : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
### Encryption in flight (TLS / SSL)
data di encrypted sebelum dikirim dan didecrypted setelah receiving, TLS certificates membantu encryption (HTTPS), Encryption in flight ensures no MITM (man in the middle attack) bisa terjadi.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/eda71a53-633a-42f8-9d26-6f028d7a29c8)

### Server-side encryption at rest
Data is encrypted setelah diterima diserver dan disimpan dengan aman dan data akan didecrypted sebelum dikirim ke client.
Mereka tersimpan dalam bentuk terenkripsi berkat key (data key). The encryption / decryption keys must be managed somewhere, and the server must have access to it.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/77367f32-31db-49a9-b720-d26c141e3a54)

### Client-side encryption
data di encrypted/decrypted di client, server tidak pernah bisa melakukannya. data akan didecrypted ketika diterima oleh client.The server should not be able to decrypt the data.
Memanfaatkan Envelope Encryption.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1f83bed9-bded-44b5-858f-0e92f7a09d62)

### AWS KMS (Key Management Service)
Anytime you hear “encryption” for an AWS service, it’s most likely KMS, AWS manages encryption keys for us.
Fully integrated with IAM for authorization, Easy way to control access to your data. Able to audit KMS Key usage using CloudTrail.
Ter-intregasi secara mulus ke most AWS services (EBS, S3, RDS, SSM…). Never ever store your secrets in plaintext.
> KMS Key Encryption also available through API calls (SDK, CLI) and Encrypted secrets can be stored in the code / environment variables.

#### KMS Keys Types
Symmetric (AES-256 keys)
- Single encryption key that is used to Encrypt and Decrypt 
- AWS services that are integrated with KMS use Symmetric CMKs 
- You never get access to the KMS Key unencrypted (must call KMS API to use)

Asymmetric (RSA & ECC key pairs)
- Public (Encrypt) and Private Key (Decrypt) pair 
- Used for Encrypt/Decrypt, or Sign/Verify operations 
- The public key is downloadable, but you can’t access the Private Key unencrypted 
> Use case: encryption outside of AWS by users who can’t call the KMS API

Types of KMS Keys :
- AWS Owned Keys (free): SSE-S3, SSE-SQS, SSE-DDB (default key)
- AWS Managed Key: free (aws/service-name, example: aws/rds or aws/ebs)

> Customer managed keys created in KMS &  imported (must be symmetric key) mempunyai harga sama yaitu  $1 / month +  pay for API call to KMS ($0.03 / 10000 calls)

Automatic Key rotation :
AWS-managed KMS Key automatic every 1 year, Customer-managed KMS Key (must be enabled) automatic every 1 year. Imported KMS Key only manual rotation possible using alias.

Key Policies : 
Control access to KMS keys, “similar” to S3 bucket policies, Difference: you cannot control access without them.
- Default KMS Key Policy
Created if you don’t provide a specific KMS Key Policy and Complete access to the key to the root user = entire AWS account.

- Custom KMS Key Policy
Define users, roles that can access the KMS key. Define who can administer the key and Useful for cross-account access of your KMS key

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1e44de3e-705c-43f9-8404-fbed4b036895)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/5ed01fe9-f9a0-4daf-9f6d-0cc3dc269891)

### KMS Multi-Region Keys
Identical KMS keys in different AWS Regions yang dapat digunakan secara bergantian. Multi-Region keys have the same key ID, key material, automatic rotation. Encrypt in one Region and decrypt in other Regions. No need to re-encrypt or making cross-Region API calls. KMS Multi-Region are NOT global (Primary + Replicas). Each Multi-Region key is managed independently.

> Use cases: global client-side encryption, encryption on Global DynamoDB, Global Aurora.

#### DynamoDB Global Tables and KMS MultiRegion Keys Client-Side encryption
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/dc8949b5-a74c-4a75-8e34-c83b94f3b605)

We can encrypt specific attributes client-side in our DynamoDB table using the Amazon DynamoDB Encryption Client, Combined with Global Tables, the client-side encrypted data is replicated to other regions.
If we use a multi-region key, replicated in the same region as the DynamoDB Global table, then clients in these regions can use lowlatency API calls to KMS in their region to decrypt the data client-side. 
> Using client-side encryption we can protect specific fields and menjamin hanya decryption jika client has access to an API key.

#### Global Aurora and KMS Multi-Region Keys Client-Side encryption
We can encrypt specific attributes client-side in our Aurora table using the AWS Encryption SDK. Combined with Aurora Global Tables, the client-side encrypted data dan direplikasi ke other regions. If we use a multi-region key, replicated in the same region as the Global Aurora DB, then clients in these regions can use low-latency API calls to KMS in their region to decrypt the data client-side.Using client-side encryption we can protect specific fields and menjamin hanya decryption if the client has access to an API key, we can protect specific fields even from database admins.

#### S3 Replication Encryption Considerations
Unencrypted objects and objects encrypted with SSE-S3 are replicated by default, Objects encrypted with SSE-C (customer provided key) can be replicated.

For objects encrypted with SSE-KMS, you need to enable the option, 
- Tentukan Kunci KMS mana yang akan mengenkripsi objek dalam bucket target
- Sesuaikan Kebijakan Kunci KMS untuk kunci target
- Peran IAM dengan kms : Decrypt untuk KMS Key sumber dan kms:Encrypt untuk KMS Key target
- Anda mungkin mendapatkan kesalahan pembatasan KMS, dalam hal ini Anda dapat meminta peningkatan Service Quotas

> You can use multi-region AWS KMS Keys, but they are currently treated as independent keys by Amazon S3 (the object will still be decrypted and then encrypted)

AMI Sharing Process Encrypted via KMS
1. AMI n Source Account is encrypted with KMS Key from Source Account
2. Must modify the image attribute to add a Launch Permission yang sesuai dengan akun AWS target yang ditentukan
3. Harus membagikan Kunci KMS yang digunakan untuk mengenkripsi snapshot AMI references dengan target account / IAM Role
4. The IAM Role/User in the target account must have the permissions to DescribeKey, ReEncrypted, CreateGrant, Decrypt
5. When launching an EC2 instance from the AMI, optionally the target account can specify a new KMS key in its own account to re-encrypt the volumes.

### SSM Parameter Store
- Secure storage for configuration and secrets
- Optional Seamless Encryption using KMS
- Serverless, scalable, durable, easy SDK
- Version tracking of configurations / secrets
- Security through IAM
- Notifications with Amazon EventBridge
- Integration with CloudFormation

Store Hierarchy
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/14600cd8-7789-4dd2-9a8b-e076c3e5e936)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/4eb5daf2-c51d-4e39-9424-841a30dc5456)

Parameters Policies : 
Allow to assign a TTL to a parameter (expiration date) to force updating or deleting sensitive data such as passwords and can assign multiple policies at a time.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1fe668a1-c95e-46d7-930f-30b7bab0ba16)

### AWS Secrets Manager
Newer service, meant for storing secrets, Capability to force rotation of secrets every X days.
Automate generation of secrets on rotation (uses Lambda), Integration with Amazon RDS (MySQL, PostgreSQL, Aurora). Secrets are encrypted using KMS and Mostly meant for RDS integration.

#### Multi-Region Secrets
Replicate Secrets across multiple AWS Regions, Secrets Manager menjaga read replica tetap sinkron dengan primary secret. Kemampuan promote a read replica Secret to a standalone Secret.
> use case : multi-region apps, disaster recovery strategies, multi-region DB…
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/878e8a83-6d8d-4c09-9d27-67201a9c4201)

### AWS Certificate Manager (ACM)
easily provision, manage, and deploy TLS certificates. Provide in-flight encryption for websites (HTTPS). Supports both public and private TLS certificates.
Free of charge for public TLS certificates and Automatic TLS certificate renewal.Cannot use ACM with EC2 (can’t be extracted).

Integrations with (load TLS certificates on) : Elastic Load Balancers (CLB, ALB, NLB), CloudFront Distributions, APIs on API Gateway.

Requesting Public Certificates
1.  List domain names to be included in the certificate
- Fully Qualified Domain Name (FQDN): corp.example.com 
- Wildcard Domain: *.example.com
2. Select Validation Method: DNS Validation or Email validation
- DNS Validation is preferred for automation purposes 
- Email validation will send emails to contact addresses in the WHOIS database 
- DNS Validation will leverage a CNAME record to DNS config (ex: Route 53)
3. It will take a few hours to get verified
4. The Public Certificate will be enrolled for automatic renewal
- ACM automatically renews ACM-generated certificates 60 days before expiry

Importing Public Certificates
- Option to generate the certificate outside of ACM and then import it
- No automatic renewal, must import a new certificate before expiry
- ACM sends daily expiration events mulai 45 days sebelum expiration 
  - The # of days can be configured 
  - Events muncul in EventBridge
- AWS Config has a managed rule named acm-certificate-expiration-check to check for expiring certificates (configurable number of days)


![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/d9eba0ae-e70d-4f63-b9a0-1da70379d09c)


### API Gateway - Endpoint Types 
- Edge-Optimized (default) - For global clients : Requests are routed through the CloudFront Edge locations (improves latency) and API Gateway still lives in only one region
- Regional : For clients within the same region and Could manually combine with CloudFront (more control over the caching strategies and the distribution) 
- Private : Can only be accessed from your VPC using an interface VPC endpoint (ENI) and Use a resource policy to define access.

### ACM – Integration with API Gateway
1. Create a Custom Domain Name in API Gateway. 
2. Edge-Optimized (default): For global clients
- Permintaan dirutekan melalui lokasi CloudFront Edge (meningkatkan latensi)
- API Gateway masih hanya ada di satu wilayah
- Sertifikat TLS harus berada di wilayah yang sama dengan CloudFront, di us-east-1
- Kemudian siapkan data CNAME atau (lebih baik) A-Alias di Route 53

3. Regional:
- Untuk klien dalam wilayah yang sama
- Sertifikat TLS harus diimpor di API Gateway, di wilayah yang sama dengan API Stage
- Kemudian siapkan data CNAME atau (lebih baik) A-Alias di Route 53

### AWS WAF – Web Application Firewall
Protects your web applications from common web exploits (Layer 7), Deploy on
- Application Load Balancer
- API Gateway
- CloudFront
- AppSync GraphQL API
- Cognito User Pool

Define Web ACL (Web Access Control List) Rules : 
- IP Set: up to 10,000 IP addresses – use multiple Rules for more IPs
- HTTP headers, HTTP body, or URI strings Protects from common attacks - SQL injection and Cross-Site Scripting (XSS)
- Size constraints, geo-match (block countries)
- Rate-based rules (to count occurrences of events) – for DDoS protection

> Web ACL are Regional except for CloudFront, A rule group is a reusable set of rules that you can add to a web ACL

Fixed IP while using WAF with a Load Balancer
WAF does not support the Network Load Balancer (Layer 4) kita bisa menggunakan Global Accelerator for fixed IP and WAF on the ALB.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/75e4fd6e-eb30-4e6c-803f-feb84887e50b)

### AWS Shield: protect from DDoS attack
DDoS: Distributed Denial of Service – many requests at the same time, 
AWS Shield Standart : 
- Free service that is activated for every AWS customer 
- Provides protection from attacks such as SYN/UDP Floods, Reflection attacks and other layer 3/layer 4 attacks

AWS Shield Advanced: 
- Optional DDoS mitigation service ($3,000 per month per organization)
- Protect against more sophisticated(canggih) attacks on Amazon EC2, Elastic Load Balancing (ELB), Amazon CloudFront, AWS Global Accelerator, and Route 53
- 24/7 access to AWS DDoS response team (DRP)
- Melindungi dari biaya yang lebih tinggi selama lonjakan penggunaan akibat DDoS
- Shield Advanced automatic application layer DDoS mitigation automatically creates, evaluates and deploys AWS WAF rules to mitigate layer 7 attacks

### AWS Firewall Manager
manage rules disemua account di AWS Organization, security policy :
- WAF rules (Application Load Balancer, API Gateways, CloudFront)
- AWS Shield Advanced (ALB, CLB, NLB, Elastic IP, CloudFront)
- Security Groups for EC2, Application Load BAlancer and ENI resources in VPC
- AWS Network Firewall (VPC Level)
- Amazon Route 53 Resolver DNS Firewall
- Policies are created at the region level

< Rules are applied to new resources as they are created (good for compliance) across all and future accounts in your Organization

WAF vs. Firewall Manager vs. Shield
- WAF, Shield and Firewall Manager are used together for comprehensive protection
- Define your Web ACL rules in WAF
- For granular protection (perlindungan menyeluruh) of your resources, WAF alone is the correct choice.
- if you want to use AWS WAF across accounts, accelerate WAF configuration, automate the protection of new resources, use Firewall Manager with AWS WAF
- Shield Advanced adds additional features on top of AWS WAF, such as dedicated support from the Shield Response Team (SRT) and advanced reporting.
- jika sering mengalami serangan DDoS attacks, pertimbangkan untuk membeli Shield Advanced

### AWS Best Practices for DDoS Resiliency
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/f6f9f6d7-09ed-4871-b2b6-18f295e5f85d)

Edge Location Mitigation : 
- BP1 - Cloudfront : Web Application delivery at the edge AND Protect from DDoS Common Attacks (SYN floods, UDP reflection…)
- BP2 - Global Accelerator : Access your application from the edge, Integration with Shield for DDoS protection, and Helpful if your backend is not compatible with CloudFront.
- BP3 - Route53 : Domain Name Resolution at the edge and DDoS Protection mechanism.

Best pratices for DDoS mitigation : 
- Infrastructure layer defense (BP1, BP3, BP6) : Protect Amazon EC2 against high traffic and  includes using Global Accelerator, Route 53, CloudFront, Elastic Load Balancing
- Amazon EC2 with Auto Scaling (BP7) : Helps scale in case jika ada lonjakan traffic secara tiba-tiba including a flash crowd or a DDoS attack
- Elastic Load Balancing (BP6) : Elastic Load Balancing scales with the traffic increases and will distribute the traffic to many EC2 instances.

Application Layer Defense : 
Detect and filter malicious web requests (BP1, BP2) : 
- CloudFront cache static content and serve it from edge locations, protecting your backend
- AWS WAF is used on top of CloudFront and Application Load Balancer to filter and block requests based on request signatures
- Aturan berbasis tarif WAF dapat secara otomatis memblokir IP pelaku jahat
- Use managed rules on WAF to block attacks based on IP reputation,or block anonymous Ips

Shield Advanced (BP1, BP2, BP6) : automatic application layer DDoS mitigation automatically creates, evaluates and deploys AWS WAF rules to mitigate layer 7 attacks

Attack surface reduction : 
- Obfuscating AWS resources (BP1, BP4, BP6) : Using CloudFront, API Gateway, Elastic Load Balancing to hide your backend resources (Lambda functions, EC2 instances)
- Security groups and Network ACLs (BP5) : Use security groups and NACLs to filter traffic based on specific IP at the subnet or ENI-level and Elastic IP are protected by AWS Shield Advanced
- Protecting API endpoints (BP4) : Hide EC2, Lambda, elsewhere. Edge-optimized mode, or CloudFront + regional mode (more control for DDoS). WAF + API Gateway: burst limits, headers filtering, use API keys.


### Amazon GuardDuty
membantu menemukan ancaman secara cerdas untuk melindungi AWS account anda. Uses Machine Learning algorithms, anomaly detection, 3rd party data. One click to enable (30 days trial), no need to install software. Input data includes : 
- CloudTrail events logs : unusual API calls, unauthorized deployments.
	- CloudTrail Management Events – create VPC subnet, create trail, …
	- CloudTrail S3 Data Events – get object, list objects, delete object, …
- VPC Flow Logs – unusual internal traffic, unusual IP address
- DNS Logs – compromised EC2 instances sending encoded data within DNS queries
- Optional Features – EKS Audit Logs, RDS & Aurora, EBS, Lambda, S3 Data Events

Can setup EventBridge rules to be notified jika ada temuan, EventBridge rules can target AWS Lambda or SNS, and Can protect against CryptoCurrency attacks (has a dedicated “finding” for it).

### Amazon Inspector
service yang menjalankan penilaian security secara otomatis pada beberapa hal, Reporting & integration with AWS Security Hub. Send findings to Amazon Event Bridge
- EC2 instance :
- memanfaatkan WS System Manager (SSM) agent
- Analyze against unintended network accessibility
- Analyze the running OS against known vulnerabilities

- For Container Images push to Amazon ECR : Assessment of Container Images as they are pushed
- For Lambda Functions : Identifies software vulnerabilities in function code and package dependencies & Assessment of functions as they are deployed

> Remember: only for EC2 instances, Container Images & Lambda functions

Continuous scanning of the infrastructure, only when needed, Package vulnerabilities (EC2, ECR & Lambda) – database of CVE, Network reachability (EC2), and A risk score is associated with all vulnerabilities for prioritization.

### AWS Macie
Amazon Macie is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover and protect your sensitive data in AWS.Macie helps identify and alert you to sensitive data, such as personally identifiable information (PII)
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/9cd3e0ac-6183-457f-a234-d7f4b3858ed4)

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1750889450555519041)







