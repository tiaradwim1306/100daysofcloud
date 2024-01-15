# AWS Storage Extras : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
#### AWS Snow Family 
Perangkat portabel yang sangat aman untuk mengumpulkan dan memproses data di edge, serta memigrasikan data ke dalam dan ke luar AWS
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/865b1c8b-dedb-4503-9eb3-186051f5c664)

#### Snowball Edge (for data transfers) : 
Physical data transport solution: move TBs or PBs of data in or out of AWS,Alternative to moving data over the network. Pay per data transfer job.
Use cases: large data cloud migrations, DC decommission, disaster recovery

#### AWS Snowcone & Snowcone SSD : 
Small, portable computing, anywhere, rugged & secure, withstands harsh environments. 
Snowcone – 8 TB of HDD Storage, Snowcone SSD – 14 TB of SSD Storage
Use Snowcone where Snowball does not fit, Can be sent back to AWS offline, or connect it to internet and use AWS DataSync to send data.

#### AWS Snowmobile : 
Transfer exabytes of data (1 EB = 1,000 PB = 1,000,000 TBs), Each Snowmobile has 100 PB of capacity. Better than Snowball if you transfer more than 10 PB
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/8118fb09-a8e1-4757-81da-85687b181965)

#### AWS OpsHub
to use Snow Family devices, you needed a CLI, now you can use AWS OpsHub (a software you install on your computer / laptop) to manage your Snow Family Device. 
Unlocking and configuring single or clustered devices, Launching and managing instances running on Snow Family Devices. Monitor device metrics and Launch compatible AWS. services on your devices (ex: Amazon EC2 instances, AWS DataSync, Network File System (NFS))

#### Snowball into Glacier : 
You must use Amazon S3 first, in combination with an S3 lifecycle policy
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/97a449e7-9151-4035-83b9-a29cb691677f)

#### Amazon FSx for Windows (File Server)
FSx for Windows is a fully managed Windows file system share drive,Supports SMB protocol & Windows NTFS. Can be mounted on Linux EC2 instances.
Scale up to 10s of GB/s, millions of IOPS, 100s PB of data, Can be accessed from your on-premises infrastructure (VPN or Direct Connect).Can be configured to be Multi-AZ and backup daily ke S3.

#### Amazon FSx for Lustre 
Lustre is a type of parallel distributed file system, for large-scale computing.Can “read S3” as a file system and can write output komputasi back to S3 melalui FSx.
Dapat digunakan dari server lokal (VPN atau Direct Connect).
use case : Video Processing, Financial Modeling, Electronic Design Automation

#### Amazon FSx for NetApp ONTAP
Managed NetApp ONTAP on AWS,file system yang kompatibel dengan protokol NFS, SMB, iSCSI.Move workloads running on ONTAP or NAS to AWS. 
storage bertambah dan mengurang secara otomatis, Snapshots, replication, low-cost, compression and data de-duplication. Kloning seketika dalam waktu tertentu (berguna untuk testing new workloads)

#### Amazon FSx for OpenZFS
Managed OpenZFS file system on AWS, File System compatible with NFS (v3, v4, v4.1, v4.2).Move workloads running on ZFS to AWS. Up to 1,000,000 IOPS with < 0.5ms latency.
Snapshots, compression and low-cost. Kloning seketika dalam waktu tertentu (berguna untuk testing new workloads)

#### Hybrid Cloud for Storage
sebagian infrastruktur di cloud dan sebagian di lokal. disebabkan oleh : Long cloud migrations, Security requirements, Compliance requirements, IT strategy.
S3 is a proprietary storage technology trus gimana mengekspos data S3 lokal? gunakan AWS storage gateway.

#### AWS storage gateway
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/a8f1e11f-7dbd-49ac-b2f8-377d92ae40db)

menjembatani antara on-promises data dan cloud data, Use cases: disaster recovery, backup & restore,tiered storage,on-premises cache & low-latency files access

Type of storage gateway : 
- <b>S3 file gateway</b>,bisa diakses dengan NFS dan SMB. data recently used disimpan dalam cache di gateway file.Transition to S3 Glacier using a Lifecycle Policy. Akses bucket menggunakan IAM role untuk setiap File Gateway.SMB Protocol has integration with Active Directory (AD) for user authentication
- <b>FSx file gateway</b>, Native access to Amazon FSx for Windows File Server. local cache untuk  frequently accessed data. Useful for group file shares and home directories
- <b>volume gateway</b>, Block storage using iSCSI protocol backed by S3. didukung EBS snapshot yang bisa restore on-premises volumes.entire dataset is on premise, scheduled backups to S3
- <b>tape gateway</b>, With Tape Gateway, companies use the same processes but, in the cloud. back up data using existing tape-based processes (and iSCSI interface).
Works with leading backup software vendors.

#### AWS Transfer Family : 
A fully-managed service for file transfers into and out of Amazon S3 or Amazon EFS using the FTP protocol.Managed infrastructure, Scalable, Reliable, Highly Available (multi-AZ).
integrate with existing authentication systems (Microsoft Active Directory, LDAP, Okta, Amazon Cognito, custom). Usage: sharing files, public datasets, CRM, ERP

#### AWS DataSync : 
move data dalam jumlah besar dari (on-promises/other cloud to AWS and AWS to AWS)
Replication tasks can be scheduled hourly, daily, weekly. File permissions and metadata are preserved.One agent task can use 10 Gbps, can setup a bandwidth limit

Storage Comparison : Summary
- S3: Object Storage
- S3 Glacier: Object Archival
- EBS volumes: Network storage for one EC2 instance at a time
- Instance Storage: Physical storage for your EC2 instance (high IOPS)
- EFS: Network File System for Linux instances, POSIX filesystem
- FSx for Windows: Network File System for Windows servers
- FSx for Lustre: High Performance Computing Linux file system
- FSx for NetApp ONTAP: High OS Compatibility
- FSx for OpenZFS: Managed ZFS file system
- Storage Gateway: S3 & FSx File Gateway, Volume Gateway (cache & stored), Tape Gateway
- Transfer Family: FTP, FTPS, SFTP interface on top of Amazon S3 or Amazon EFS
- DataSync: Schedule data sync from on-premises to AWS, or AWS to AWS
- Snowcone / Snowball / Snowmobile: to move large amount of data to the cloud, physically
- Database: for specific workloads, usually with indexing and querying

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1746794081819464186)
