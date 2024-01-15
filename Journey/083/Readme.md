# Database v1 : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
### RDS
RDS adalah Relational Database service, managed DB service for DB, use SQL as a query language.
database that managed by AWS is Postgres, MySQL, MariaDB, Oracle, Microsoft SQL Server, Aurora (AWS Proprietary database)

kelebihan menggunakan RDS daripada baut database di EC2 : 
- Automated provisioning, OS patching
- Continuous backups and restore to specific timestamp (Point in Time Restore)!
- Monitoring dashboards
- Read replicas for improved read performance
- Multi AZ setup for DR (Disaster Recovery)
- Maintenance windows for upgrades
- Scaling capability (vertical and horizontal)
- Storage backed by EBS (gp2 or io1)
> note : BUT you can’t SSH into your instances

#### RDS auto scaling 
membantu untuk increase storage di RDS DB instance secara otomatic, ketika RDS mendeteksi kamu running out dari free database storage maka akan scales otomatis.Karena database discale secara otomatis maka set maximum storage threshold atau maximum limit untuk DB storage.
sangat bagus untuk applications dengan unpredictable workloads, dan support semua RDS database engine  (MariaDB, MySQL, PostgreSQL, SQL Server, Oracle)

#### RDS Read Replica 
untuk read scalability digunakan untuk scale read replica, example jika kita punya satu apps yang terhubung dengan RDS maka apps tersebut akan melakukan read and write ke RDS, read replica ini lah yang membantu RDS untuk menerima banyak request.
per RDS bisa membuat sampai 15 Read Replica, within AZ, cross AZ, Cross region.
read replica bersifat ASYNC, sehingga reads bisa konsisten.
read replica bisa membuat DB nya sendiri dan aplikasi harus update connection string untuk memanfaatkan read replica.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/7cf6d72b-9d30-46e2-a210-d2e8b61b4fed)

> read replica hanya bisa digunakan untuk READ gak bisa INSERT UPDATE atau DELETE

RDS Custom → managed Oracle dan Microsoft SQL database dengan OS dan database customization, akses ke database dan OS yang mendasarinya sehingga Anda bisa : 
- Configure settings
- Install patches
- Enable native features
- Access the underlying EC2 Instance using SSH or SSM Session Manager.

Nonaktifkan automation mode untuk melakukan customization, better to take a DB snapshot before

#### RDS vs. RDS Custom
- RDS: entire database and the OS to be managed by AWS
- RDS Custom: full admin access to the underlying OS and the databas

#### Amazon Aurora 
database proprietary form AWS (not open source).
menggunakan Postgres dan Mysql, Aurora is “AWS cloud optimized” and claims 5x performance improvement over MySQL on RDS, over 3x the performance of Postgres on RDS.
storage aurora otomatis bertambah sebesar 10GB hingga 128TB. bisa memiliki sampai 15 read replica dan lebih cepat dibandingkan mysql, failover aurora terjadi seketika dan asli HA (High Availablity).<b>MAHAL 20% DIBANDINGKAN RDS NAMUN LEBIH EFISIEN</b>

6 copies data across 3 AZ : 
- 4 copies out of 6 untuk write
- 3 copies out of 6 untuk reads
- self healing (penyembuhan mandiri) dengan peer-to-peer replication
- Penyimpanan dibagi menjadi 100 volume
Automated failover for master in less than 30 seconds, Master + up to 15 Aurora Read Replicas melayani reads, Support for Cross Region Replication

<b>feature aurora</b> : Automatic fail-over, Backup and Recovery, Isolation and security, Industry compliance, Push-button scaling, Automated Patching with Zero Downtime, Advanced Monitoring, Routine Maintenance, Backtrack: restore data at any point of time without using backups

#### ASG Aurora Replica
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1b71ff57-7d72-495d-bbd9-4e7e6d7fc9e1)

ketika lonjakan request semakin naik maka read replica akan scale out dengan otomatis

#### Custom Endpoints
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/d8c17c29-75b5-434b-b39c-1f9b85d51256)

Custom Endpoint adalah cara dimana kita membagi read perfomance di read replica yang lebih besar

#### Aurora serverless 
- Automated database instantiation dan auto scaling based on actual usage
- Good for infrequent, intermittent or unpredictable workloads
- no capacity planning needed and pay per second agar lebih hemat biaya

<b>Aurora Machine Learning</b> memungkinkan add ML-based predictions to your applications via SQL. Simple, optimized, and secure integration between Aurora and AWS ML services.
> support service : sagemaker, comprehend
> use case : deteksi penipuan, penargetan iklan, analisis sentimen, rekomendasi produk

#### RDS Backup 
- Automated backup : Daily full backup of the database, Transaction logs are backed-up by RDS every 5 minutes, restore to any point in tim (kapanpun), 
- Manual Backup : manual karena users, Penyimpanan cadangan selama yang Anda inginkan.
use case : stopped RDS tetep berbayar, jika dihentikan dalam waktu yang lama take a snapshot dan restore untuk mengembalikannya

<b>Aurora Database Cloning</b> memungkinkan create a new aurora DB cluster dari yang sudah ada. 
use copy-on-write protocol (new DB cluster menggunakan data yg sama dengan DB cluster yang lebih fast and efficient), When updates are made to the new DB cluster data, then additional storage is allocated and data is copied untuk dipisahkan.
<b>Useful to create a “staging” database from a “production” database without impacting the production database</b>

#### RDS & Aurora Security
- at-rest : encryption using KMS, jika master tidak di encrypt maka read replica tidak bisa diencrypt, To encrypt an un-encrypted database, go through a DB snapshot & restore as encrypted
- in-flight encryption : TLS-reads by default
- IAM authentication : roles untuk connect ke database
- security groups : control network access
- no ssh available : kecuali RDS custom 
- Audit Logs can be enabled and sent to CloudWatch Logs for longer retention

#### RDS Proxy 
fully managed database proxy for RDS, allow app mengumpulkan dan berbagi koneksi DB yang dibuat dengan database, Meningkatkan efisiensi database dengan mengurangi stress pada database resource (misalnya CPU, RAM) dan meminimalkan open connections (and timeouts) 
- serverless, auto scaling and HA (multi-AZ), reduced RDS & aurora failover time by up 66%
- Supports RDS (MySQL, PostgreSQL, MariaDB, SQL Server) and Aurora (MySQL, PostgreSQL)
- RDS Proxy tidak pernah dapat diakses secara publik (harus diakses dari VPC)

#### Amazon ElastiCache
service to managed redis or memcached, chaced di in-memory databases dengan high performance and low latency.
- help reduce beban database untuk read intensive workloads, Membantu membuat aplikasi Anda tidak memiliki kewarganegaraan. 
- AWS menangani OS maintenance or patching, optimizations, setup, configuration, monitoring, failure recovery and backups
  
<b> Penggunaan ElastiCache melibatkan banyak perubahan kode aplikasi</b>

<b>DB chace</b> → aplikasi akan meminta request pada ElastiChace jika elastichace tidak available maka akan request langsung ke RDS.fungsinya meringankan load pada RDS.

<b>Cache</b> harus memiliki invalidation strategy untuk memastikan hanya current data yang digunakan di sana.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/ddc98495-9f70-424e-8d51-546de636ec01)
<b>User Sessions Store</b> : 
ketika user login disalah satu apps, app akan menulis session data di ElastiChace ketika user mengakses another instance makan akan mengambil data dari user yang sudah login.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/dc68aa4e-408b-4251-a233-06d2e3121a38)

#### ElastiCache – Cache Security
ElastiCache supports IAM Authentication for Redis, IAM policies on ElastiCache are only used for AWS API-level security. 
- Redis : set a password/token, extra level of security for your cache, Support SSL in flight encryption.
- Memcached : Supports SASL-based authentication (advanced)

> redis use case : Gaming Leaderboards, Kumpulan Redis Sorted menjamin keunikan dan urutan elemen, Setiap kali elemen baru ditambahkan, elemen tersebut diberi peringkat secara real-time, lalu ditambahkan urutan yang benar

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1746765447041867966)


