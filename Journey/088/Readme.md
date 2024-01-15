# AWS Integration & Messaging : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Introduction
ketika deploy multiple applications, mereka membutuhkan komunikasi satu sama lain,Ada dua pola komunikasi aplikasi yaitu Synchronous communications (application to application) dan Asynchronous / Event based (application to queue to application) .

## Cloud Research
### Amazon SQS
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/5164be0d-d2ab-40a3-a948-548a1c404784)

Fully managed service, used to decouple applications, Attributes: 
- Unlimited throughput, sehingga bisa mengirim sebanyak apapun message 
- Default berada di antrian adalah selama 4 days, maximum of 14 days 
- Low latency (<10 ms on publish and receive) 
- Limitation of 256KB per message sent
> Can have duplicate messages, Dapat menerima pesan yang tidak berurutan

<b>producing message</b> : Produced to SQS using the SDK, Pesan tersebut disimpan di SQS sampai konsumen menghapusnya. SQS standard: unlimited throughput, 
Consuming Messages : Consumers (running on EC2 instances, servers, or AWS Lambda, etc), Poll SQS for messages (receive up to 10 messages at a time). Delete the messages using the DeleteMessage API.

<b>Multiple EC2 Instances Consumers</b> : Konsumen menerima dan memproses pesan secara paralel, Konsumen menghapus pesan setelah memprosesnya, Kita dapat menskalakan konsumen secara horizontal untuk meningkatkan hasil pemprosesan

<b>SQS to decouple between application tiers</b>: menghubungkan antara frontend dan backend, dimana SQS akan menjadi penerima pesan dari frontend dan mengirim pesan tersebut ke backend
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/42b1f6f7-60db-4192-af7d-6b33df1c3a3a)

#### Amazon SQS - Security
- Encryption : 
  - in-flight encryption using HTTPS API 
  - At-rest encryption using KMS keys 
  - Client-side encryption if the client wants to perform encryption/decryption itself 
- Access Controls: IAM policies to regulate access to the SQS API
- SQS Access Policies - useful untuk cross account acces ke SQS bucket, useful untuk allow service lainnya

#### SQS – Message Visibility Timeout
Setelah sebuah pesan disurvei oleh konsumen, pesan tersebut menjadi tidak terlihat oleh konsumen lain.Secara default, “batas waktu visibilitas pesan” adalah 30 detik yang artinya pesan mempunyai waktu 30 detik untuk diproses, After the message visibility timeout is over, the message is “visible” in SQS

#### Long Polling 
adalah pesan yang muncul ketika konsumen meminta pesan dari antrian, ia akan memilih untuk ‘wait’ pesan tiba jika tidak ada pesan dalam antrian. 
Long Polling mengurangi jumlah API calls yang dilakukan ke SQS sekaligus meningkatkan efisiensi dan mengurangi latensi aplikasi Anda, Waktu tunggu bisa antara 1s hingga 20s.
Long polling can be enabled at the queue level or at the API level using WaitTimeSeconds

#### FIFO Queue (First In First Out)  
yaitu ordering of messages in the queue. Limited throughput: 300 msg/s without batching, 3000 msg/s with, Kemampuan mengirim tepat sekali (dengan menghapus duplikat). Pesan diproses secara berurutan oleh konsumen.
> use case : SQS with Auto Scaling Group, SQS with database, SQS as a buffer to database writes,SQS to decouple between application tiers

### SNS 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/25204482-9cb3-4f48-8a38-4277f93a4844)

The “event producer” only sends message to one SNS topic, As many “event receivers” (subscriptions) as we want to listen to the SNS topic notifications.
Each subscriber to the topic will get all the messages (note: new feature to filter messages)
Up to 12,500,000 subscriptions per topic and 100,000 topics limit.
- Topic Publish (using the SDK) : Create a topic,create subscription, publish to the topic
- Direct Publish (for mobile apps SDK)  : Create a platform application,Create a platform endpoint,Publish to the platform endpoint, and Works with Google GCM, Apple APNS, Amazon ADM

#### SNS - security 
- Encryption: 
  - In-flight encryption using HTTPS API 
  - At-rest encryption using KMS keys 
  - Client-side encryption if the client wants to perform encryption/decryption itself 
- Access Control :  IAM policies to regulate access to the SNS API
- SNS Access Policies (similar to S3 bucket policies) : Useful for cross-account access to SNS topics and Useful for allowing other services ( S3…) to write to an SNS topic

#### SNS + SQS: Fan Out
Tekan sekali di SNS, terima di semua antrian SQS yang menjadi pelanggan,Terpisah sepenuhnya, tidak ada kehilangan data. SQS allows for: data persistence, delayed processing and retries of work. Kemampuan untuk menambah lebih banyak pelanggan SQS dari waktu ke waktu.Make sure your SQS queue access policy allows for SNS to write. Cross-Region Delivery: works with SQS Queues in other regions
> If you want to send the same S3 event to many SQS queues, use fan-out

#### Amazon SNS – FIFO Topic 
FIFO = First In First Out (ordering of messages in the topic), punya 2 fitur : ordering by Message Group ID (all messages in the same group are ordered) and Deduplication using a Deduplication ID or Content Based Deduplication.
> bisa mempunyai SQS standart dan FIFO queue sebagai subscribers, limited throughput sama kaya SQS

<b>Message Filtering</b> : JSON policy digunakan untuk memfilter pesan yang dikirim ke SNS topic’s subscriptions.  If a subscription doesn’t have a filter policy maka akan receives every message.

#### Kinesis
Makes it easy to collect, process, and analyze streaming data in real-time, menyerap realtime data seperti Application logs, Metrics, Website clickstreams, IoT telemetry data
terdiri dari 4 layanan : 
- Kinesis Data Streams: capture, process, and store data streams.
Kemampuan untuk memproses ulang (replay) data,Setelah data dimasukkan ke Kinesis, data tersebut tidak dapat dihapus, Data yang berbagi partisi yang sama akan masuk ke shard yang sama.
  - Producers: AWS SDK, Kinesis Producer Library (KPL), Kinesis Agent
  - Consumers: Write your own: Kinesis Client Library (KCL), AWS SDK and Managed: AWS Lambda, Kinesis Data Firehose, Kinesis Data Analytics, 
> security : control access with IAM policies,Encryption in flight using HTTPS endpoints and Encryption at rest using KMS,VPC Endpoints available for Kinesis to access within VPC

- Kinesis Data Firehose: load data streams into AWS data stores
Fully Managed Service, no administration, automatic scaling, serverless and Pay for data going through Firehose.Supports many data formats, conversions, transformations, compression.Supports custom data transformations using AWS Lambda. Can send failed or all data to a backup S3 bucket.
- Kinesis Data Analytics: analyze data streams with SQL or Apache Flink.
- Kinesis Video Streams: capture, process, and store video streams

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/c7469021-21f6-4c86-b703-eb41c3b032ad)

#### Amazon MQ
managed message broker service for rabbitMQ and activeMQ, MQ doesn’t scale as much as SQS and SNS. MQ run on server and run in multi AZ with failover

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1746799219397259718)



