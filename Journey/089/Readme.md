# Container on AWS : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Introduction
<b>Docker</b> adalah software development platform yang digunakan untuk deploy apps.
apps dikemas dalam containers yang dapat dijalankan di OS manapun dengan cara yang sama dimanapun apps dijalankan.
> use case : microservices architecture, lift-and-shift apps from on- premises to the AWS cloud, …

- Public Docker repository : Docker Hub (https://hub.docker.com)
- AWS : Amazon ECR, can to be private repository and public repository

## Cloud Research
### Architecture : Virtual Machine VS Container
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/6d5b025e-09ec-4f0e-b354-ece666d89f21)

#### Dockerfile 
adalah sebuah file teks yang berisi serangkaian instruksi yang digunakan untuk membuat Docker image, docker ini bisa dipush atau diupload di Docker Hub atau ECR. image yang sudah dipush ini bisa di pull atau didownload dan dijalankan menjadi container
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/8ea7ef93-758d-4e1b-a091-222ea880e728)

#### Docker Containers Management on AWS
- Amazon Elastic Container Service (Amazon ECS) → amazon’s container platform
- Amazon Elastic Kubernetes Service (Amazon EKS) → amazon manages kubernetest (open source)
- AWS Fargate → serverless container platform, work with ECS and EKS

### Amazon ECS
Cluster terdiri dari e2 instance, sehingga ketika kita launch cluster kita harus maintenance ec2 instancenya. Tapi ketika kita launch cluster menggunakan fargate kita tidak perlu manage EC2 instance semuanya menjadi serverless dan kita hanya membuat task definitions.

Data Volumes (EFS) adalah file system yang dimount ke ECS Task, use case : penyimpanan bersama (persistent storage) multi-AZ.S3 <b>cann’t be mounted as a file system.</b>

#### Scaling dibagi menjadi 3 : 
- Target tracking → menskalakan berdasarkan nilai target untuk metrik CloudWatch tertentu
- Step scaling → scaled berdasarkan CloudWatch Alarm yang ditentukan
- Scheduled scaling → scaled berdasarkan date/time tertentu (perubahan yang dapat diprediksi)

#### ECS Task by Event Bridge
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/0204639f-df44-4711-8456-20351fbcb76a)

when client upload image ke S3 maka akan membuat eventbridge, amazon eventbridge akan membuat rule ke ECS task agar bisa get object ke S3 sehingga setiap ada object baru ke S3 maka akan tercatat di dynamodb.

### Amazon ECR
store and manage Docker images on AWS, fully integrated with ECS, and access nya dicontrol oleh IAM (permission error → policy). support image Supports image vulnerability scanning, versioning, image tags, image lifecycle.

### EKS Node Types : 
- Managed node groups, create and manage node(ec2 instance) for you, node are part of an ASG, support on demand or spot instances
- Self-Managed Nodes, node create by you and registered to EKS cluster manage by ASG, use prebuild AMI, and support on-demand or spot instances
- AWS Fargate, no maintenance required; no nodes managed → serverless

### AWS App Runner
fully managed service that makes it easy to deploy web applications 
and APIs at scale, tidak membutuhkan infrastructure required, start 
dengan source code atau container image, otomatis build and deploy 
web app, otomatis scaling, HA, Load balancer, encryption. 
Connect to database, cache, and message queue services.
- ECR public = https://gallery.ecr.aws/ , jika app runner pilih docker https://gallery.ecr.aws/docker 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/5282bec4-4af9-48eb-bb1d-531cc6eb0969)

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1746804762769830112)
