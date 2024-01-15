# S3 : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
Amazon S3 Use cases 
- Backup and storage 
- Disaster Recovery 
- Archive 
- Hybrid Cloud storage 
- Application hosting 
- Media hosting 
- Data lakes & big data analytics 
- Software delivery 
- Static website

<b>Bucket</b> : Amazon S3 allows people to store objects (files) in “buckets” (directories), bucket harus mempunyai global uniq name, bucket defined at the region level. S3 looks like a global service but buckets are created in a region 

<b>Object</b> : file have key,maksimal object is 5TB, jika upload diatas 5GB gunakan “multipart-upload”.
- The key is the FULL path: 
  - s3://my-bucket/my_file.txt 
  - s3://my-bucket/my_folder1/another_folder/my_file.txt 
- The key is composed of prefix + object name
  - s3://my-bucket/my_folder1/another_folder/my_file.txt

#### S3 - Security 
- user based : IAM policies 
- resource based : bucket policies, object ACL, bucket ACL
> Note: an IAM principal can access an S3 object if 
  > - The user IAM permissions ALLOW it OR the resource policy ALLOWS it 
  > - AND there’s no explicit DENY
- encrypt objects in Amazon S3 using encryption keys


![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/c512dfa5-89f6-4d24-8719-b43352c68d2d)

#### Amazon S3 – Static Website Hosting
S3 bisa host static website dan bisa diakses di internet, If you get a 403 Forbidden error, make sure the bucket policy allows public reads

#### Amazon S3 - Versioning
membuat version files di S3, enabled di bucket level, best practice untuk version your bucket (Melindungi dari penghapusan yang tidak disengaja dan Easy roll back to previous version).
sebelum mengaktifkan versioning maka versinya adalah null, suspend versioning tidak menghapus versi sebelumnya

#### Amazon S3 – Replication (CRR & SRR)
harus mengaktifkan versioning di source dan destination bucket, 
- Cross-Region Replication (CRR) 
- Same-Region Replication (SRR)
> bucket bisa dibeda aws akun, copying is asynchronous, Harus memberikan izin IAM yang sesuai ke S3

use case : 
- CRR : compliance, lower latency access, replication across accounts
- SRR : log aggregation, live replication between production and test accounts

>setelah direplicate maka hanya object baru yang akan ter-replica. optional jika ingin replica existing object using S3 batch replication 

untuk delete, bisa replica delete marker dari source ke target tapi Deletions with a version ID are not replicated.
bukan <b>‘chaining’</b> jika kita replica bucket1 ke bucket2 dan bucket2 punya replica ke bucket3 maka object dibucket1 tidak akan tereplica dibucket3

#### S3 Storage Classes 
- Amazon S3 Standard - General Purpose 
99.99% Availability, digunakan untuk frequently accessed data, low latency and high throughput. Use Cases: Big Data analytics, mobile & gaming applications, etc
- Amazon S3 Standard-Infrequent Access (IA) 
Untuk data yang jarang diakses, namun memerlukan akses cepat bila diperlukan, lebih murah daripada S3 standart. Use cases: Disaster Recovery, backups
- Amazon S3 One Zone-Infrequent Access 
sama seperti IA namun High durability (99.999999999%) in a single AZ; data lost jika sengaja dihapus, Use Cases: Storing secondary backup copies of on-premises data, or data you can recreate
- Amazon S3 Glacier Instant Retrieval 
Penyimpanan objek berbiaya rendah yang dimaksudkan untuk pengarsipan / pencadangan, Pengambilan milidetik, bagus untuk data yang diakses sekali dalam seperempat.Durasi penyimpanan minimal 90 hari
- Amazon S3 Glacier Flexible Retrieval 
digunakan untuk pengarsipan / pencadangan,Dipercepat (1 hingga 5 menit), Standar (3 hingga 5 jam), Massal (5 hingga 12 jam) – gratis, Durasi penyimpanan minimal 90 hari
- Amazon S3 Glacier Deep Archive 
Standar (12 jam), Massal (48 jam), Durasi penyimpanan minimal 180 hari
- Amazon S3 Intelligent Tiering 
move object otomatis berdasarkan penggunaannya, cost yang kecil.

> Can move between classes manually or using S3 Lifecycle configurations

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/711c921f-912f-4427-944b-59784d2a904d)

>b>Moving between Storage Classes</b> : untuk object yang jarang diakses pindahkan ke standar IA,untuk archive yang tidak membutuhkan akses cepat move ke Glacier or Glacier Deep Archive. <b>moving object otomatis dengan lifecycle rules.</b>

#### Amazon S3 – Lifecycle Rules
configure objects to transition to another storage class, Move objects to Standard IA class 60 days after creation. Move to Glacier for archiving after 6 months, configure objects to expire (delete) after some time. Access log files can be set to delete after a 365 days
bisa digunakan untuk menghapus file versi lama jika versioning diaktifkan

<b>Storage Class Analysis</b> : membantu memutuskan kapan object akan dipindahkan ke storage class yang tepat.Recommendations for Standard and Standard IA.Does NOT work for One-Zone IA or Glacier. laporan diperbarui setaip hari. Good first step to put together Lifecycle Rules

<b>S3 Event Notifications</b> : umpama kita ingin menghasilkan thumbnail gambar yang diunggah ke S3 dan membuat event dan notification di SNS,SQS,atau lambda function. dan bisa dibuat sebanyak yang diiginkan.

<b>S3 – Baseline Performance</b> : Amazon S3 automatically scales to high request rates, latency 100-200 ms. Jika Anda menyebarkan pembacaan ke keempat prefiks secara merata, Anda dapat mencapai 22.000 permintaan per detik untuk GET dan HEAD

<b>Multi-part upload</b> : recommended for file diatas 100MB dan digunakan untuk file diatas 5GB. Dapat membantu memparalelkan upload (speed up transfers)

<b>S3 Transfer Acceleration</b> : speed transfer dengan transfer file ke aws edge yang nantinya akan meneruskannya ke S3 bucket di target region.Compatible with multi-part upload
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/522c8f10-ee8b-45f7-961c-0342a7a47c89)

S3 Byte-Range Fetches : digunakan untuk mempercepat download, digunakan untuk download failure dengan membagi beberapa byte yang akan didownload menjadi beberapa bagian.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/88bb3575-2d7c-4ca2-992f-aebee382e145)

<b>S3 Select & Glacier Select</b> : ambil lebih sedikit data dengan SQL menggunakan server-side filtering, bisa difilter berdasarkan rows & columns (simple SQL statements). Lebih sedikit transfer jaringan, lebih sedikit biaya CPU di sisi klien

#### 3 Batch Operations : 
melakukan operasi massal pada existing S3 objects dengan single request,example : 
- Modify object metadata & properties
- Copy objects between S3 buckets
- Encrypt un-encrypted objects
- Modify ACLs, tags
- Restore objects from S3 Glacier
- Invoke Lambda function to perform custom action on each object

job consists of a list of objects, the action to perform, and optional parameters. 
S3 Batch Operations manages retries, tracks progress, sends completion notifications, generate reports, etc. You can use S3 Inventory to get object list and use S3 Select to filter your objects.

#### Object Encryption : 
encrypt object using one of 4 methods : 
- Server-Side Encryption (SSE)
  - SSE with Amazon S3-Managed Keys (SSE-S3) - key milik AWS. Enabled by default for new buckets & new objects.
  - SSE with KMS Keys stored in AWS KMS (SSE-KMS) - gunakan KMS untuk mengelolanya. KMS advantages: user control + audit key usage using CloudTrail
  - SSE with Customer-Provided Keys (SSE-C) - mengelola encryption keys sendiri by the customer outside of AWS, S3 tidak akan menyimpan key yang kamu sediakan. Encryption key must provided in HTTP headers, for every HTTP request made.
- Client-Side Encryption (CSE)
Use client libraries such as Amazon S3 Client-Side Encryption Library, client must encrypt data themselves before sending to Amazon S3, Clients must decrypt data themselves when retrieving from Amazon S3. Customer fully manages the keys and encryption cycle
- Encryption in transit (SSL/TLS)
encryption di flight bisa disebut SSL/TLS, HTTP Endpoint – non encrypted and HTTPS Endpoint – encryption in flight.

#### CORS Cross-Origin Resource Sharing)
mekanisme berbasis web browser untuk mengijinkan requests to other origins while visiting the main origin.
> origin terdiri dari skema (protokol) + host (domain) + port

The requests won’t be dipenuhi unless the other origin allows for the requests, using CORS Headers (example: Access-Control-Allow-Origin)

example use case : 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/3bc133ac-4dbc-43e7-9ccc-78b4b46d34d6)

html dan asset mempunyai bucket destination yang berbeda untuk itu kita gunakan CORS untuk request nya agar web browser bisa ambil asset dari bucket-asset

MFA Delete 
force users to generate a code on a device (usually a mobile phone or hardware) before doing important operations on S3.versioning harus enabled.
> MFA will be required to : Permanently delete an object version,Suspend Versioning di bucket

MFA won’t be required to: Enable Versioning, List deleted versions. Only the bucket owner (root account) can enable/disable MFA Delete

#### S3 Access Logs 
untuk mencatat semua akses ke bucket S3, Permintaan apa pun yang dibuat ke S3, dari akun mana pun, diizinkan atau ditolak, akan masuk ke bucket S3 lain.
Data tersebut dapat dianalisis menggunakan alat analisis data, The target logging bucket must be in the same AWS region.

#### Pre-Signed URL : 
Generate pre-signed URLs using the S3 Console, AWS CLI or SDK. url expiration : 1 - 720 menit. users diberikan pre-sign url yang sudah digenerated dengan permissions GET / PUT.
Examples:
- Allow only logged-in users to download a premium video from your S3 bucket
- Allow an ever-changing list of users to download files by generating URLs dynamically
- Allow temporarily a user to upload a file to a precise location in your S3 bucket

S3 Glacier Vault Lock
object dimasukkan ke S3 glacier fault dan kemudian Anda menguncinya sehingga tidak dapat dimodifikasi atau dihapus.Kunci kebijakan untuk pengeditan di masa mendatang (tidak dapat diubah atau dihapus lagi). Helpful for compliance and data retention. Memblokir penghapusan versi objek selama jangka waktu tertentu, 2 mode retention : 
- Retention mode - Compliance: 
  - Object versions can't be overwritten or deleted by any user, including the root user 
  - Objects retention modes can't be changed, and retention periods can't be shortened
- Retention mode - Governance: 
  - Most users can't overwrite or delete an object version or alter its lock settings 
  - Some users have special permissions to change the retention or delete the object 
- Retention Period: protect the object for a fixed period, it can be extended

#### Access Points : 
menyederhanakan security management for S3 Buckets,Kita dapat menentukan access point agar dapat diakses hanya dari dalam VPC. Anda harus membuat VPC Endpoint untuk mengakses Access Point (Gateway or Interface Endpoint). VPC Endpoint Policy must allow access to the target bucket and Access Point

#### S3 Object Lambda 
gunakan AWS lambda function untuk merubah objek sebelum diambil oleh caller application. Hanya diperlukan satu bucket S3, yang didalamnya kita membuat S3 access point dan S3 Object Lambda Access Points..

Use Cases: 
- Menyunting informasi identitas pribadi untuk lingkungan analitik atau non-produksi.
- Mengonversi berbagai format data, seperti mengonversi XML ke JSON.
- Mengubah ukuran dan watremaking images dengan cepat menggunakan detail spesifik penelepon, seperti pengguna yang meminta objek tersebut.

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1746788670064185570)



