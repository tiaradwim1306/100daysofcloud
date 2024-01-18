# Data & Analytics : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
### Amazon Athena
Serverless query service untuk menganalisis data yang tersimpan di S3, use standart SQL Language to query the file. Support CSV, JSON, ORC, Avro, and Parquet.
pricing $5.00 per TB data scanned,
Biasa digunakan dengan Amazon Quicksight untuk reporting/dashboard.
> use case : Business intelligence / analytics / reporting, analyze & query VPC Flow Logs, ELB Logs, CloudTrail trails, etc...

use columnar data for cost-saving, compress data for smaller retrievals, partition datasets S3 for easy querying on virtual columns. Use larger files > 128 MB to minimize overhead

#### Amazon Athena – Federated Query : 
- Allows you to run SQL queries across data stored in relational, non-relational, object, and custom data sources (AWS or on-premises)
- Uses Data Source Connectors that run on AWS Lambda to run Federated Queries (e.g., CloudWatch Logs, DynamoDB, RDS, …)
- Store the results back in Amazon S3

### RedShift
RedShift is based on postgrest, but it’s not used for OLTP (Online Transaction Processing), tapi untuk OLAP (Online analytical processing) digunakan untuk analytics and data warehousing.
10x better performance than warehouse karena bisa scale to PBs of data, bentuk data seperti kolom bukan tabel dan paralel disetiap query nya, Pay as you go based on the instances provisioned.
has a SQL interface for performing the queries, Integrate Amazon Quicksight atau Tableu.

#### RedShift Cluster : 
- leader node digunakan untuk query planning dan hasil pengumpulan
- compute node digunakan untuk performing the queries and send result to leader

> anda harus menyediakan node size terlebih dahulu dan bisa menggunakan reserved instance for cost savings

#### Snapshots & DR
have multi-AZ mode untuk beberapa cluster, snapshot adalah point-in-time backups of a cluster, disimpan secara internal di S3.
snapshot bersifat incremental (hanya perubahan yang disimpan), bisa direstore kedalam new cluster. bisa menyalin snapshot secara otomatis dari sebuah cluster ke another aws region.
- automated backup : every 8 hours, every 5 GB, or on a schedule. Set retention between 1 to 35 days
- manual backup : snapshot disimpan hingga Anda menghapusnya

#### Redshift Spectrum
query data sudah masuk S3 tanpa loading, harus memiliki Redshift cluster available untuk memulai query, query tsb kemudian diserahkan ke ribuan redshift Spectrum nodes.

### Amazon OpenSearch
amazon opensearch adalah service yang digunakan untuk search any field bahkan yang cocok sebagian di DynamoDB.
mempunyai 2 mode : managed cluster and serverless cluster.
tidak mendukung SQL namun bisa diaktifkan via a plugin, bisa menelan data dari Kinesis data farehouse, AWS IoT, and cloudwatch logs. Security nya melalui cognito & IAM, KMS encryption, TLS.

### Amazon EMR (Elastic MapReduce)
digunakan untuk menganalisis dan meproses data yang sangat banyak/besar. EMR dibuat oleh ribuan EC2 instance.
EMR dibundle dengan banyak tools seperti apache spark, HBase, Presto, Flink. EMR menangani semua penyediaan dan konfigurasi dan mempunyai penskalaan otomatis dan terintegrasi dengan spot instance.
purchasing option : on-demand, reserved, spot instances.
Use cases : data processing, machine learning, web indexing, big data…

terdiri daro beberapa node : 
- Master Node: Manage the cluster, coordinate, manage health – long running
- Core Node: Run tasks and store data – long running
- Task Node (optional): Just to run tasks – usually Spot

### QuickSight
Business Intelligence yang didukung serverless machine learning to create interactive dashboards.Fast, automatically scalable, embeddable, with per-session pricing.
> use case : Business analytics, Building visualizations, Perform ad-hoc analysis, Get business insights using data

integrated dengan RDS, Aurora, Athena, Redshift, S3, etc. In-memory computation using SPICE engine jika data diimport ke QuickSight.
Enterprise edition: memungkinkan setup Column-Level security (CLS).

### AWS Glue
service yang digunakan untuk extract, transform, and load atapun bisa disebut ETL service,
useful to prepare and transform data for analytics. fully serverless service
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/b67f57f0-868a-43ed-9b63-f41ef495e674)

example : jika anda ingin data yang berada di S3 Bucket dan RDS dimuat kedalam redshift data warehouse anda bisa menggunakan Glue.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/4d234073-f8bb-438a-b81f-39899f232a31)

example : anda mempunyai bucket input dimana disana mempunyai file CSV, menggunakan GLUE kita akan mengkonversi CSV ke parquet dan memasukkannya ke S3 output, sehingga memudahkan athena untuk menganalisis data di S3 output

#### Glue on high-level
- Glue Job Bookmarks: prevent re-processing old data
- Glue Elastic Views:
- Combine and replicate data across multiple data stores using SQL
- No custom code, Glue monitors for changes in the source data, serverless
- Leverages a “virtual table” (materialized view)
- Glue DataBrew: clean and normalize data using pre-built transformation
- Glue Studio: new GUI to create, run and monitor ETL jobs in Glue
- Glue Streaming ETL (built on Apache Spark Structured Streaming): compatible with Kinesis Data Streaming, Kafka, MSK (managed Kafka)

### AWS Lake Formation
central place untuk menyimpan semua data untuk tujuan analytics, Fully managed service yang memudahkan data lake dalam hitungan hari.
Discover, cleanse, transform, and ingest data into your Data Lake. Combine structured and unstructured data in the data lake. Out-of-the-box source blueprints: S3, RDS, Relational & NoSQL DB…

Fine-grained Access Control (control akses yg terperinci) untuk apps di tingkat row and column dan dibangun diatas AWS Glue.

### Kinesis Data Analytics for SQL app
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/fe7a7605-1257-4783-a185-9cf2c929e077)

example : anda bisa menganalisis data dari kinesis data stream dan kinesis data firehouse menggunakan kinesis data analytics lalu mengubahnya dengan menggunakan SQL statement untuk analisis real-time, lalu juga bisa digabungkan dengan reference data dari s3. Nah data ini bisa dikirim kemana saja seperti ke kinesis data stream ataupun ke kinesis data firehouse yang nantinya bisa dikirimkan ke service yang terintegrasi dengan service tsb.

Jadi kinesis data analytics adalah real-time analytics dari kinesis data stream & firehouse using SQL, dapat menambahkan reference data dari S3 untuk memperkaya data streaming.
fully managed and no server to provision, automatic scaling and pay for actual consumption rate.
- Output
	- kinesis data stream : create streams out dari real-time analytics query
	- kinesis ata firehouse : send analytics query results to destination

Use case : time-series analytics, real-time dashboard, real-time metrics

### Kinesis Data Analytics for Apache Flink
gunakan flink (java, scala, or SQL) untuk process and analyze streaming data, 
run any apache flink application on a managed cluster on AWS : 
- provisioning compute resources, parallel computation, automatic scaling
- application backups (implemented as checkpoints and snapshots)
- Use any Apache Flink programming features
- Flink does not read from Firehose (use Kinesis Analytics for SQL instead)

### Amazon Managed Streaming for Apache Kafka (Amazon MSK)
alternatif dari aws kinesis, fully managed apache kafka on AWS, 
- Allow you to create, update, delete clusters
- MSK creates & manages Kafka brokers nodes & Zookeeper nodes for you
- Deploy the MSK cluster in your VPC, multi-AZ (up to 3 for HA)
- Automatic recovery from common Apache Kafka failures
- Data is stored on EBS volumes for as long as you want

### MSK Serverless
- Run Apache Kafka on MSK without managing the capacity 
- MSK automatically provisions resources and scales compute & storage

> nb:  “Apache Kafka adalah penyimpanan data terdistribusi yang dioptimalkan untuk menyerap dan memproses data streaming secara real time”

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/fa95d7fb-9fce-4147-8706-60e23312590d)

example : MSK akan membuat cluster yang nanti didalam satu cluster akan ada beberapa broker, broker ini akan menerima kode dari producer yang bisa berupa AWS IoT, kinesis, RDS, and etc.Main broker akan menerima topic dari producer lalu dari main broker akan mereplica nya ke semua broker jika sudah tereplika ke semua broker baru akan memprosess dan mengirimkannya ke berbagai tujuan seperti S3, EMR, SageMaker, etc.

### Big Data Ingestion Pipeline
we want ingestion (penyerapan) pipeline fully serverless, collect data in real time, transform the data, query the transformed data using SQL, reports created using the queries should be in S3 and We want to memuat data ke warehouse and create dashboards.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/a8963179-21a2-40fa-9b8a-bda7d10f2db9)

summary Big Data Ingestion Pipeline Scenario : 
- IoT Core allows you to harvest(mengambil) data from IoT devices
- Kinesis is great for real-time data collection
- Firehose helps with data delivery to S3 in near(hampir) real-time (1 minute)
- Lambda can help Firehose with data transformations
- Amazon S3 can trigger notifications to SQS
- Lambda can subscribe to SQS (we can have connecter S3 to Lambda)
- Athena is a serverless SQL service and results are stored in S3
- The reporting bucket contains analyzed data and can be used by reporting tools such as AWS QuickSight, Redshift, etc…

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1747807972246659117)
