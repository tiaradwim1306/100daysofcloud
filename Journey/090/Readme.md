# Serverless : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Introduction
serverless is a paradigma dimana developer tidak perlu mengelola servers lagi,
mereka hanya deloy code, hanya deploy function. 
Serverless == FaaS (Function as a Service),
> Serverless bukan berarti tidak ada server tapi berarti tidak manage menyediakan atapun melihatnya.

## Cloud Research
### Serverless service AWS : 
- lambda
- SNS & SQS
- dynamodb			  
- Kinesis Data Firehose
- cognito			    
- Aurora Serverless
- API gateway			
- step function
- S3
- fargate

### Lambda 
virtual functions and no server to manage, limited by time, run on-demand, and scaling automated.
> benefit : easy pricing, integrated dengan seluruh aws service, integrated dengan banyak programming languages, easy monitoring dgn Cloudwatch, Meningkatkan RAM will also improve CPU and network!

#### Lambda SnapStart, When you publish a new version: 
- Lambda initializes your function 
- Takes a snapshot of memory and disk state of the initialized function 
- Snapshot is cached for low-latency access

#### CloudFront Functions : For high-scale, latency-sensitive CDN customizations, use to change viewer request and responses : 
- viewer request : setelah cloudfront menerima requesr dari viewer.
- viewer response : sebelum clooudfront meneruskan respons ke viewer.

#### Lambda VPC 
secara default Lambda function is launched outside your own VPC, sehingga VPC tidak mungkin bisa mengakses RDS, ElastiCache, internal ELB,...

> Maka dari itu kita bisa memasukan lambda function kedalam VPC, dan lambda create ENI in your subnet.

#### RDS Invoking Lambda - RDS Proxy
jika lambda bisa mengakses database secara langsung maka akan membuka banyak koneksi, untuk itu kita membutuhkan RDS proxy. benefit : 
- improve scalability dengan mengumpulkan dan sharing DB connection
- improve availability dengan mengurangi failover time and preserving connetions
- improve security dengan menerapkan IAM authentication and storing credential in secret manager


### DynamoDB
fully managed, HA with replication across multiple AZ. NoSQL Database yang support transaksi. Scales to massive workloads, distributed database. Low cost and auto-scaling capabilities. No maintenance or patching, always available.
> tersedia 2 Table Class yaitu Standart dan Infrequent Access (IA) Table Class.

dynamodb made of table, setiap table mempunyai primary key dan memiliki jumlah item yang tidak terbatas.Setiap item memiliki atribut yang null atau dapat ditambah seiring waktu.
tipe data yang didukung berupa : 
- scalar type : string, number, binary, boolean, null
- document type : list, map
- set type : string set, number set, binary set

#### R/W capacity mode : 
- provisioned mode (default): specify bumber of read/write per second, plan capacity beforehand, pay for provisioned RCU & WCU, possibility untuk add ASG mode.predictable workloads.
- on-demand mode : 
r/w otomatis scale up/down, no capacity planning needed, pay for wha you use (more expensive), great for unpredictable workloads,lonjakan tiba” yg curam.

#### Advance Features : 
DAX (DynamoDB Accelerator), fully manage, ketika banyak antrian melakukan read table maka DAX akan membuat cluster untuk mengatasi kemacetan dengan melakukan chacing data.dengan latency microsecond untuk cached data, tidak require application logic modification.

#### DynamoDB Global Tables 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/08d7c468-c833-4cc4-ae36-b4007da21bd4)

ketika suatu table disetting global table maka mereka akan saling mereplikasi 2 arah sehingga bisa saling write 2 table tersebut. Sehingga membuat table accessible dan low latency in multiple regions, active - active replication, apps bisa read and write ditable manapun. <b>Must enable DynamoDB Streams</b>

#### TTL DynamoDB 
otomatis delete items after expiry timestamp, ada table expired time sehingga ketika sudah waktunya expired item akan nonaktif dan terhapus setelah beberapa saat setelahnya.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/d24f7f41-0784-4943-bf03-af160a316e47)

> Use cases: reduce stored data dengan hanya menyimpan current items, mematuhi kewajiban peraturan, web session 
handling

#### DynamoDB - Backup for disaster recovery
- Continuous backups using point-in-time recovery (PITR) : enabled 35 hari, pemulihan tepat waktu kapan saja dengan backup window, recovery process creates a new table.

- On-demand backups : full backup untuk penyimpanan jangka panjang, hingga dihapus secara eksplisit, Tidak memengaruhi performance and latency, dapat dikelola oleh AWS Backup, recovery process creates a new table

### Building a Serverless API
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/8717ff47-a812-484b-a103-54da8dc47a8a)

client akan mengakses public API gateway yang nantinya akan ketrigger di lambda dan lambda akan meneruskan data tersebut ke dynamodb

### AWS API GATEWAY
- Lambda + API gateway = no infrastructure to manage
- support websocket protocol, 
- handle API versioning, 
- handle different environments (dev, test, prod…), 
- Handle security (Authentication and Authorization)
- create API keys, tangani pembatasan permintaan

#### API Gateway - Integrations high level
- Lambda Function, invoke lambda function, easy way untuk expose rest api 
- HTTP, expose HTTP enspoint in backend, example : internal HTTP API on-premise and ALB. 
- AWS Service : menggunakan AWS service yang lain sebagai objectnya, example : start an AWS Step Function workflow, post a message to SQS.

#### Endpoint Type : 
- Edge Optimized(default): for global client, request dirutekan melalui CloudFront edge locations, API Gateway berada di one region
- Regional: for client with same region, can manually combine with CloudFront
- Private: only accessed from your VPC dengan interface VPC endpoint (ENI), use a resource policy to define access.

### AWS Step Function
Build serverless visual workflow untuk mengatur lambda function. features : sequence, parallel, conditions, timeouts, error handling, etc.
Can integrate with EC2, ECS, On-premises servers, API Gateway, SQS queues, etc.
> memungkinkan menerapkan fitur human approval, use case : order fulfillment, data processing, web applications, any workflow

### AWS Cognito
give users and identity untuk berinteraksi dengan web atau mobile application, mempunyai 2 jenis layanan : 
- Cognito user pools : sign in untuk app users, integrate with API gateway & ALB
- Cognito Identity Pools (Federated Identity) : menyediakan AWS credentials untuk user sehingga mereka bisa mengakses AWS resource secara langsung. integrate dengan cognito user pool as an identity provider.

Cognito User Pools (CUP) – User Features
- create serverless database of user for your web and mobile apps
- simple login : username / email / password combination
- password reset
- email & phone number verification
- MFA
- federated identities : users from facebook. google, dll

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1747173885278331349)





