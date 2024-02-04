# More Solutions Architecture And White Papers & Architectures : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
## More Solutions Architecture
### Event Processing in AWS
#### Lambda, SNS & SQS
Banyak sekali event processing yang bisa dipilih, bisa menggunakan SQS dan SNS dengan skenario yang berbeda seperti dibawah ini

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/fe62c2f2-d2a7-4990-a4ae-4a299805b533)

#### Fan Out Pattern: deliver to multiple SQS
bagaimana jika kita ingin mengirim message ke multiple SQS, dari aplikasi langsung ke SQS secara bergantian bisa namun nanti akan terjadi crash sehingga kita bisa menggunakan SNS sebagai penghubung ditengahnya yang fungsinya untuk menjembatani message dari aplikasi ke SQS. System ini disebut Fan Out Pattern.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/2c2178a6-ea1f-4cc7-9865-16cdf61a12f7)

#### S3 Event Notifications
notification bisa berisi S3:ObjectCreated, S3:ObjectRemoved, S3:ObjectRestore, S3:Replication, etc. BIsa menggunakan object name filtering seperti (*.jpg). Kita bisa membuat banyak S3 event yang kita inginkan, bisa menggunakan SNS,SQS, atapun lambda. S3 event notifications biasanya mengirim event dalam hitungan detik but sometimes take a minute or longer.
> Use case :  generate thumbnails of images uploaded to S3

S3 Event Notifications with Amazon EventBridge

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/4ef12abf-3461-4505-a147-d036637d001f)

- Advanced filtering options with JSON rules (metadata, object size, name...), 
- Multiple Destinations – ex Step Functions, Kinesis Streams / Firehose…
- EventBridge Capabilities – Archive, Replay Events, Reliable delivery

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/64b6fc35-e4ef-4ac9-b278-a1be575326a1)

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/416f4cba-547e-4e1a-8ebd-0d696305e413)


