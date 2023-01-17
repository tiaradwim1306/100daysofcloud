
# Database Part 2 : Course on Udemmy by Stepahane Mareek

## Introduction
There are many types of databases besides RDS, ElastiCache and also DynamoDB,there are several databases that we will study in this journey :
- Redshift 
- EMR
- Athena
- Amazon QuickSight
- DocumentDB
- Amazon Neptune
- Amazon QLDB
- Amazon Managed Blockchain
- AWS Glue
- DMS

## Cloud Research

### Redshift 
- based on PostgreSQL, but not used for OLTP
- OLAP is used for analytics and data storage
- loading data every hour
- 10x better performance than other databases and scales up to PBs of data
- Data column storage
- MPP and high available
- pay according to the instance you use
- has a SQL interface to perform queries
- integrated with BI

### EMR (Elastic MapReduce)
- EMR is not database,EMR helps creating Hadoop clusters (Big Data) to analyze and process vast amounts of data
- The clusters can be made of hundreds of EC2 instances
- Also supports Apache Spark, HBase, Presto, Flink…
- EMR takes care of all the provisioning and configuration
- Auto-scaling and integrated with Spot instances
- Use cases: data processing, machine learning, web indexing, big data…

### Athena 
- Serverless query service to analyze data stored in Amazon S3
- Uses standard SQL language to query the files
- Supports CSV, JSON, ORC, Avro, and Parquet (built on Presto)
- Pricing: $5.00 per TB of data scanned
- Use compressed or columnar data for cost-savings (less scan)
- Use cases: Business intelligence / analytics / reporting, analyze & query VPC Flow Logs, ELB Logs, CloudTrail trails, etc...

### Amazon QuickSight
- Serverless machine learning-powered business intelligence service tocreate interactive dashboards
- Fast, automatically scalable, embeddable, with persession pricing
- Use cases:
	- Business analytics
	- Building visualizations
	- Perform ad-hoc analysis
	- Get business insights using data
- Integrated with RDS, Aurora,Athena, Redshift, S3…

### DocumentDB
- Aurora is an “AWS-implementation” of PostgreSQL / MySQL …
- DocumentDB is the same for MongoDB (which is a NoSQL database)
- MongoDB is used to store, query, and index JSON data
- Similar “deployment concepts” as Aurora
- Fully Managed, highly available with replication across 3 AZ
- DocumentDB storage automatically grows in increments of 10GB, up to 64 TB.
- Automatically scales to workloads with millions of requests per seconds

### Amazon Neptune
- Fully managed graph database 
- A popular graph dataset would be a social network 
	- Users have friends 
	- Posts have comments 
	- Comments have likes from users 
	- Users share and like posts…
- Highly available across 3 AZ, with up to 15 read replicas 
- Build and run applications working with highly connected datasets – optimized for these complex and hard queries
- Can store up to billions of relations and query the graph with milliseconds latency
- Highly available with replications across multiple AZs 
- Great for knowledge graphs (Wikipedia), fraud detection,recommendation engines, social networking

### Amazon QLDB (Quantum Ledger Database)
- A ledger is a book recording financial transactions
- Fully Managed, Serverless, High available, Replication across 3 AZ
- Used to review history of all the changes made to your application data over time
- Immutable system: no entry can be removed or modified, cryptographically verifiable
- 2-3x better performance than common ledger blockchain frameworks, manipulate data using SQL
- Difference with Amazon Managed Blockchain: no decentralization component, in accordance with financial regulation rules

### Amazon Managed Blockchain
- Blockchain makes it possible to build applications where multiple parties can execute transactions without the need for a trusted, central authority.
- Amazon Managed Blockchain is a managed service to:
- Join public blockchain networks
- Or create your own scalable private network
- Compatible with the frameworks Hyperledger Fabric & Ethereum

### AWS Glue 
- Managed extract, transform, and load (ETL) service 
- Useful to prepare and transform data for analytics 
- Fully serverless service 
- Glue Data Catalog: catalog of datasets 
- can be used by Athena, Redshift, EMR

### DMS (Database Migration Service)
- Quickly and securely migrate databases to AWS, resilient, self healing
- The source database remains available during the migration
- Supports:
	- Homogeneous migrations: ex Oracle to Oracle
	- Heterogeneous migrations: ex Microsoft SQL Server to Aurora


## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1615216180612198403)
