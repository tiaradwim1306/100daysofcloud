
# Cloud Integration 

## Introduction 
When we start deploying multiple applications, they inevitably need to communicate with each other

There are two patterns of application communication
- Synchronous communications (application to application)
- Asynchronous / Event based (application to queue to application)

If you are used to encoding 10 videos then suddenly need 1000 then Synchronous between apps can be problematic due to sudden spikes in traffic

In this case, it's best to separate your applications:
- use SQS: queuing model
- using SNS: pub/sub mode
- using Kinesis: real-time data streaming models


## Cloud Research

### SQS (Simple Queue Service)
SQS Queue is a liaison between producers and consumers which does not only consist of 1 producer/consumer but can be more.

Standart Queue :
- Fully managed service (serverless), use to decouple applications
- No limit to how many messages can be in the queue and messages are deleted after they’re read by consumers
- low latency
- Consumers share the work to read messages & scale horizontally


### Amazon Kinesis - real time big data streaming
Managed service to collect, process, and analyze real-time streaming
data at any scale

Additional info :
- Kinesis Data Streams: low latency streaming to ingest data at scale from hundreds of thousands of sources
- Kinesis Data Firehose: load streams into S3, Redshift, ElasticSearch, etc…
- Kinesis Data Analytics: perform real-time analytics on streams using SQL
- Kinesis Video Streams: monitor real-time video streams for analytics or ML

### Amazon SNS
if we want to send one message to many receivers it will be difficult if we send one by one for that we can use Amazon SNS

- The “event publishers” only sends message to one SNS topic
- As many “event subscribers” as we want to listen to the SNS topic notifications
- Each subscriber to the topic will get all the messages
- Up to 12,500,000 subscriptions per topic, 100,000 topics limit

### Amazon MQ
Amazon MQ is a managed message broker service for RabbitMQ nad ActiveMQ
- Amazon MQ doesn’t “scale” as much as SQS / SNS
- Amazon MQ runs on servers, can run in Multi-AZ with failover
- Amazon MQ has both queue feature (~SQS) and topic features (~SNS)

### Summary 
SQS:
- Queue service in AWS
- Multiple Producers, messages are kept up to 14 days
- Multiple Consumers share the read and delete messages when done
- Used to decouple applications in AWS

SNS:
- Notification service in AWS
- Subscribers: Email, Lambda, SQS, HTTP, Mobile…
- Multiple Subscribers, send all messages to all of them
- No message retention

Kinesis: real-time data streaming, persistence and analysis

Amazon MQ: managed message broker for ActiveMQ and RabbitMQ in the cloud (MQTT, AMQP.. protocols)


## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1618427192987508738)
