# Route 53 & Beanstalk : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research

### Introduction
DNS → Domain Name System which translates the human friendly hostnames into the machine IP addresses
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/eb31977f-d16f-4b01-a4f2-1e99c5e776b4)

### Amazon Route 53
A highly available, scalable, fully managed and Authoritative DNS. domain register service.
Ability to check the health of your resources,  only AWS service which provides 100% availability SLA.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/db737c73-a0b9-4375-97d8-5636289725cc)

#### hosted zones : 
tempat untuk define how to route traffic to a domain and its subdomains, 
- Public Hosted Zones – contains records that specify how to route traffic on the Internet (public domain names) application1.mypublicdomain.com 
- Private Hosted Zones – contain records that specify how you route traffic within one or more VPCs (private domain names) application1.company.internal
> You pay $0.50 per month per hosted zone!

#### Route 53 – Records TTL
- higher TTL adalah  1 days hal ini menyebabkan traffic ke route 53 lebih sedikit sehingga menyebabkan recordnya outdated atau gak up to date sesuai server route 53 karena mengakses domain lewat cache.
- low TTL (60s) membuat traffic ke route53 lebih besar sehingga pembayaran juga lebih banyak,namun record akan selalu up to date sehingga gampang untuk ganti atau nambah record.Except for Alias records, TTL bersifat wajib untuk setiap data DNS

> CNAME : Points a hostname to any other hostname
> Alias : Points a hostname to an AWS Resource (root domain)

#### Alias Records
Maps a hostname to an AWS resource, Secara otomatis mengenali perubahan alamat IP resource. Tidak seperti CNAME, ini dapat digunakan untuk top node DNS seperti example.com

Alias Records Targets: 
- Elastic Load Balancers 
- CloudFront Distributions 
- API Gateway 
- Elastic Beanstalk environments 
- S3 Websites 
- VPC Interface Endpoints 
- Global Accelerator accelerator 
- Route 53 record in the same hosted zone

#### Routing Policies
Tentukan bagaimana Route 53 merespons DNS queries, DNS tidak merutekan lalu lintas apa pun, ia hanya merespons permintaan DNS.Route 53 Supports the following Routing Policies :
- Simple 
mengarahkan lalu lintas ke single resource, specify multiple values in the same record, if multiple values are returned, a random one is chosen by the client. Bila Alias diaktifkan, tentukan saja satu resource. Can’t be associated with Health Checks
- Weighted
Control the % of the requests that go to each specific resource,DNS records must have the same name and type, bisa associated with Health Checks, Assign a weight of 0 to a record to stop sending traffic to a resource. Jika semua record mempunyai bobot 0, maka semua record akan dikembalikan secara merata.Use cases: load balancing between regions, testing new application version. resource dengan weighted terbesar akan mendapat request terbanyak jua.
- Failover
otomatis failover ke EC2 secondary jika EC2 primary ternyata unhealthy.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/e8abab0d-2bed-4d81-b71e-10a2cc9680e2)
- latency based
redirect ke resource yang mempunyai latency paling kecil yg dekat dengan client, Super helpful when latency for users is a priority. latency didasarkan pada lalu lintas antara pengguna dan Wilayah AWS. Can be associated with Health Checks.
- Geolocation
<b>based user location</b>,specify location by Continent, Country or by US State. Should create a “Default” record.Can be associated with Health Checks, Use cases: website localization, restrict content distribution, load balancing
- Multi-Value Answer 
digunakan ketika routing traffic to multiple resources, Route 53 return multiple values/resources, up to 8 record dikembalikan untuk setiap Multi-Value query. Multi-Value bukan pengganti memiliki ELB
- Geoproximity (using Route 53 Traffic Flow feature)
Route traffic to your resources based on the geographic location of users and resources, bisa shift traffic ke reosurce berdasarkan bias yang ditentukan.resource : AWS resources (specify AWS region) and Non-AWS resources (specify Latitude and Longitude)
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/63d9ef5e-b013-46fd-b109-0291add420cb)

- IP-based Routing
Routing is based on clients’ IP addresses, Anda memberikan daftar CIDR untuk klien Anda dan titik akhir/lokasi yang sesuai (user-IP-to-endpoint mappings). Example: route end users from a particular ISP to a specific endpoint. Use cases: Optimize performance, reduce network costs…

<b>Health Checks</b> hanya untuk public resource, Automated DNS Failover : Health checks that monitor an endpoint, Health checks that monitor other health checks, Health checks that monitor CloudWatch Alarms Health Checks terintregasi dengan CW metric

<b>Calculated Health Checks</b> : Menggabungkan hasil beberapa Pemeriksaan Kesehatan menjadi satu Pemeriksaan Kesehatan, child health check bisa menggunakan <b>OR,AND,or NOT</b>. bisa monitor sampai 256 child health checks. Tentuka berapa banyak health checks yang harus dilewati agar parent health check bisa pass (lolos)

### Classic Solutions Architecture Discussion
#### Elastic Beanstalk Classic Solutions Architecture Discussion 
adalah developer centric view of deploying an application on AWS. menggunakan semua komponen yang pernah kita lihat sebelumnya: EC2, ASG, ELB, RDS.
Automatically handles capacity provisioning, load balancing, scaling, application health monitoring, instance configuration.
application code adalah tanggung jawab developer, dan kita masih mempunyai full control dikonfigurasi. 
> Beanstalk is free but you pay for the underlying instances.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/3bd15f82-f2d9-4ce8-8f82-92fe4cfd7c79)

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1746777136780964292)



