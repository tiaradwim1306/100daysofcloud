
# Other Compute : Course on Udemmy by Stepahane Mareek


## Cloud Research

### Docker 
Docker is a software development platform for deploying multiple applications packaged in containers that can run on any OS.
ex : EC2 instance which runs docker javascript, docker Mysql, etc.

### Docker versus Virtual Machines Architecture
![image](https://user-images.githubusercontent.com/120786669/213123569-89ec1850-8941-4604-b204-79cf59736666.png)
 

### ECS (Elastic Container Service)
- Launch Docker containers on AWS,must provision & maintain the infrastructure (the EC2 instances)
- AWS takes care of starting / stopping containers and has integrations with the Application Load Balance

### Fargate 
Launch Docker containers on AWS, no infrastructure required so it's simpler, serverless and runs AWS based on CPU/RAM required.

### ECR (Elastic Container Registry)
 ECR is a private Docker Registry on AWS, here you can store docker images and run them on ECS or Fargate

### Serverless
The new thing where developers don't need to manage servers anymore, initially serverless is FaaS (Function as a Service) pioneered by AWS Lambda.
ex: S3,DynamoDB,Lambda,Fargate

### AWS Lambda 
Lambda is Virtual functions so no servers to manage, and limited by time,on-demand runs and scaling is automated

Benefits :
- Easy Pricing
- Integrated with the whole AWS suite of services
- used only when needed
- Integrated with many programming languages
- Easy monitoring via AWS CloudWatch
- Easily get more resources per function (up to 10GB RAM!)
- Increasing RAM also increases CPU and network

note : Lambda language support is Node.js(JavaScript),Python,Java,C#,Golang,and Ruby 

practice : create AWS lambda function for stop EC2 instances 

### Amazon API Gateway
Fully managed service for developers to easily build, publish, maintain, monitor APIs and be serverless and scalable

### Batch 
- Fully managed batch processing at any scale
- Efficiently run 100,000s of computing batch jobs on AWS
- A “batch” job is a job with a start and an end (opposed to continuous)
- Batch will dynamically launch EC2 instances or Spot Instances
- AWS Batch provisions the right amount of compute / memory
- You submit or schedule batch jobs and AWS Batch does the rest!
- Batch jobs are defined as Docker images and run on ECS
- Helpful for cost optimizations and focusing less on the infrastructure

Batch vs Lambda
- Lambda: 
	- Time limit 
	- Limited runtimes 
	- Limited temporary disk space 
	- Serverless 

- Batch: 
	- No time limit 
	- Any runtime as long as it’s packaged as a Docker image 
	- Rely on EBS / instance store for disk space 
	- Relies on EC2 (can be managed by AWS)

### Amazon Lightsail
Amazon lightsail is a standalone service and great for people with little cloud experience.lightsail is AWS simplified
- can be used for virtual servers, storage, databases, and networks at low & predictable prices
- simpler than the services studied before like EC2, RDS, etc.
- Can manage notifications and resource monitoring of your Lightsail
- Use case:
	- Simple web app (has templates for LAMP, Nginx, MEAN, Node.js…)
	- Website (templates for WordPress, Magento, Plesk, Joomla)
	- Dev/Test Environment
- Has high availability but no auto-scaling, limited AWS integration

### summary 
- Docker: container technology to run applications
- ECS: run Docker containers on EC2 instances
- Fargates: Run Docker containers without provisioning the infrastructure and serverless offering (no EC2 instances)
- ECR: Private Docker Images Repository
- Batch: run batch jobs on AWS across managed EC2 instances
- Lightsail: predictable & low pricing for simple applications & DB stacks
- Lambda is Serverless, Function as a Service, seamless scaling, reactive
- Lambda Language Support: many programming languages except (arbitrary) Docker
- Lambda Invocation time: up to 15 minutes
- Lambda Use cases:
	- Create Thumbnails for images uploaded onto S3
	- Run a Serverless cron job
- API Gateway: expose Lambda functions as HTTP API

## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1615636316091449346)
