# EC2 : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek 

## Cloud Research
### EC2 FUNDAMENTAl
<b>UserData</b> adalah script data yang digunakan untuk bootstrap (launch command when a machine start) yang run dengan <b>user root</b>.
digunakan untuk mengotomatisasikan boot seperti installing updates, installing software, download common files from internet, dll
#### instance type :
- general purpose : cocok untuk workload seperti web server atau code repositories, seimbang antara compute, memory, networking
- compute optimized : cocok untuk compute-intensive task yang memerlukan high performance processors, example batch processing workload, media transcoding, high performance web server, etc
- memory optimized : fast performance untuk workloads yang memproses large data set di memory, example high performance database, distributed web scale cache stores, in-memory database optimized, etc.
- storage optimized : cocok untuk storage-intensive yang memerlukan proses raed and write access ke large data sets di local storage, example OLTP, relational & NoSQL database, cache for in-memory database

#### Security Groups 
security group adalah fundamental dari network security di AWS, sg mengontrol traffic dan mengijinkan in or out dari EC2 instance.
sg hanya berisi allow rules, reference by IP or by security group.
bisa di attach di multiple instance, 
> jika error ‘time out’ maka itu salah sg jika ‘connection refused’ itu salah aplikasi. 

all inbound traffic is blocked by default and all outbound traffic is authorized by default.

### EC2 SAA LEVEL
#### Public IP vs Private IP 
- public ip : identified on the internet, uniques across the whole web, dan mudah ditemukan
- private ip : identified on private network only, uniques across the private network, 2 different
private network can have same IP, terhubung ke internet dengan NAT, hanya beberapa range ip yang bisa digunakan di private
- Elastic IP : fixed public IP for instance yang bisa di attach kapan saja di 1 instance.

#### Placement groups : 
control strategi instance placement dengan placement groups, ada beberapa cara :  
- <b>cluster</b> : mengelompokan instance kedalam latency group di single AZ,jika rack gagal maka semua instance gagal pada waktu yang sama. use case : Big Data job that needs to complete fast and Application that needs extremely low latency and high network throughput
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/d3620e3a-5dd5-4493-83a3-a70e6db306b2)

- <b>spread</b> : menyebarkan instance keseluruh underlying hardware (max 7 instance per group per AZ). bisa dideploy ke across AZ, reduce resiko simultaneous failure,instance berada di physical hardware yang berbeda. use case : Application that needs to maximize high availability and Critical Applications where each instance must be isolated from failure from each other
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/c4096bc1-ca97-40ba-8d3e-a0d05c5b66b6)

- <b>partition</b> : menyebarkan instance ke banyak partisi yang berbeda (bergantung pada set rak yang berbeda) dalam AZ dan menskalakan hingga 100 instance per group. per AZ bisa 7 rack hingga 100-an instance.
partition failure can affect many EC2 but won’t affect other partitions. Use cases: HDFS, HBase, Cassandra,Kafka
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/70848c03-2897-4263-8533-5321c804f71e)

#### ENI adalah logical component di VPC yang mewakili virtual network card, setiap ENI mempunyai : 
- Primary private IPv4, one or more secondary IPv4
- One Elastic IP (IPv4) per private IPv4
- One Public IPv4
- One or more security groups
- A MAC address
> anda bisa create ENI dan move pada instance for failover, terikat pada spesifik AZ

#### EC2 hibernate 
- Status dalam memori (RAM) dipertahankan
- Boot instance jauh lebih cepat! (OS tidak dihentikan/di-restart)
- Di balik terpal: status RAM tertulis ke file di volume root EBS
- Volume root EBS harus dienkripsi
> use case : Long-running processing, Saving the RAM state, Services that take time to initialize

### Instance Storage
<b>EBS</b>  : network drive yang bisa diattach diinstance saat running.
Hal ini memungkinkan instance Anda untuk menyimpan data, bahkan setelah penghentiannya, terikat dengan specifik AZ dan bisa dianalogikan sebagai ‘network usb stick’.

<b>Delete On Termination</b> : by default ketika diterimante EBS volume akan terdelete, sedangkan other EBS volume tidak akan terdeleted

<b>Snapshot</b> : make backup dari EBS volume pada suatu waktu, tidak perlu detach volume namun recommended untuk mendetachnya, bisa copy snapshot across AZ Or Region
features: 
- archive : Move a Snapshot to an ”archive tier” that is 75% cheaper, need 24 to 72 hours for restoring the archive
- recycle bin : Setup rules to mempertahankan deleted snapshot sehingga bisa dipulihkan, specify retention (from 1 day to 1 year)
- restore (FSR) : Paksa inisialisasi penuh snapshot agar tidak ada latensi pada penggunaan pertama

<b>AMI</b> adalah customization of EC2 instance dimana kita menambah software, configuration, operating system, monitoring, etc. faster boot or configuration karena semua package sudah terinstall. 
AMI built untuk specific region dan bisa copied across regions, 
AMI bisa dari : PUblic AMI, AMI buatan sendiri, AWS Marketplace AMI

#### EC2 Istance Store 
EBS volume adalah network drive yang bagus tapi ‘limited’ performance jika ingin high performance disk gunakan EC2 instance.
benefit : 
- Better I/O performance 
- EC2 Instance Store lose their storage if they’re stopped (ephemeral)
- Good for buffer / cache / scratch data / temporary content
- Risk of data loss if hardware fails 
- Backups and Replication are your responsibility 

<b>EFS</b> adalah managed NFS yang bisa dimounted dibanyak EC2, work with EC2 Instance di multi-AZ. Highly available, scalable, expensive (3x gp2), pay per use.
> use cases : content management, web serving, data sharing, wordpress. etc

compatible with linux based AMI ‘NOT WINDOWS’ encrypt at rest using KMS. File system scales automatically, pay-per-use, no capacity planning

## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1746752307730202942)
