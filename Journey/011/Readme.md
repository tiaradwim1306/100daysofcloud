
# Database Part 1: Course on Udemmy by Stepahane Mareek

## Introduction
Databases are very important in cloud computing, in this journey we will learn these things :
- Database 
- RDS 
- practice RDS
- ElastiChace
- DynamoDB
- practice DynamoDB

## Cloud Research

## Introduction to Database 
Databases are optimized for a purpose and come with different features, shapes and constraints.
Storing data on disk (EFS, EBS, EC2 Instance Store, S3) has limitations, for that we need to use a database. In the database we can organize data or define relationships between data sets.

### Type of Database 
- Relational Database
like spreadsheets, we can link data to each other.
- NoSQL databases
Purpose built for specific data models and have flexible schemas for building modern applications. The benefits are Flexibility, Scalability, High performance, Highly functional
ex : JSON (JavaScript Object Notation)

### Benefits of using Database :
- Quick Provisioning, High Availability, Vertical and Horizontal Scaling
- Automated Backup & Restore, Operations, Upgrades
- Operating System Patching is handled by AWS
- Monitoring, alerting

## RDS (Relational Database Service)
Database service that uses SQL as the query language.
Allows you to create databases in the cloud managed by AWS such as :
- Postgres
- MySQL
- MariaDB
- Oracle
- Microsoft SQL Server
- Aurora (AWS Proprietary database)

### Advantages over using RDS vs using DB on EC2
- Automated provisioning, OS patching
- Continuous backups and restore to specific timestamp (Point in Time Restore)!
- Monitoring dashboards
- Read replicas for improved read performance
- Multi AZ setup for DR (Disaster Recovery)
- Maintenance windows for upgrades
- Scaling capability (vertical and horizontal)
- Storage backed by EBS (gp2 or io1)

note : you can’t SSH into your instances

### Amazon Aurora
- Aurora not open sourced 
- supports 2 database technologies, namely PostgreSQL and MySQL
- Aurora is "AWS cloud optimized"
- Aurora's storage is automatically increased in increments of 10 GB, up to 64 TB.
- Aurora is expensive than RDS but more efficient
- Not in the free tier

### RDS Deployments
- Read Replicas
Scale the read workload of your DB, can create up to 5 Read Replicas and data only written to main DB
- Multi - AZ
DB failover will be available in case of a problem in the AZ, data is only read/written to the main database, and failover is only available in 1 other AZ
- Multi Region 
create read replicas in multi-region, this is used for disaster recovery in case of region issues.
local performance for global reads, which incurs additional costs for each read replica in each region.

### practice :
- create database in RDS and then take a snapshot
- restore snapshots
- copy snapshot and change to different AZ
- share snapshots

## Amazon ElastiCache
- Same as RDS i.e. managing Relational Database
- ElastiCache is to get managed Redis or Memcached
- Caches are in-memory databases with high performance, low latency
- Helps reduce load off databases for read intensive workloads

## DynamoDB
- available with replication across 3 AZ and includes NoSQL database.
- Can be millions of requests per second, trillions of lines, 100s of TB of storage and fast and consistent in performance.
- Has low latency and integrates with IAM for security, authorization, and administration
- Low cost and auto-scaling capabilities

### DynamoDB Accelerator - DAX
- Fully Managed in-memory cache for DynamoDB
- 10x performance improvement 
- Secure, highly scalable & highly available

### DynamoDB - Global Tables
- Make a DynamoDB table accessible with low latency in multiple-regions
- Active replication (read/write to any AWS Region)

### practice :
- create table in DynamoDB
- create item and add new attribute with type string and number 
 

## Social Proof

✍️ Show that you shared your process on Twitter or LinkedIn

[Twitter](https://twitter.com/tiaradwim1306/status/1615205167942729729)
