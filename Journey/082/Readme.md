# High Availability & Scalability : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Introduction
<b>Scalability</b> berarti sebuah aplikasi atau system yang bisa handle beban yang lebih besar dengan beradaptasi.
2 scalability : vertical & horizontal
- Vertical Scalability : increasing the size, example : t2.micro to t2.large.Vertical scalability is very common for non distributed systems, such as a database.
- Horizontal Scalability : increasing the number,very common for web applications / modern applications.

## Cloud Research
### ELB
<b>ELB</b> adalah server yang forward traffic to multiple servers downstream.

<b>Health check</b> digunakan untuk memverifikasi apakah EC2 instance berfungsi dengan baik atau tidak.mengetahui instance mana yang meneruskan traffic untuk reply request mereka. health check dilakukan pada port dan route (/health common). jika response nya bukan 200 (OK) maka instance adalah unhealthy.

#### types load balancer : 
- classic load balancer : HTTP,HTTPS,TCP,SSL
- application load balancer : HTTP,HTTPS,WebSocket
- network load balancer : TCP,TLS,UDP
- gateway load balancer : operates layer 3 - IP protocol

#### ALB 
are a great fit for micro services & container-based application, has port mapping feature to redirect a dynamic port in ECS.
> target ALB : ec2 instances, ec2 tasks, lambda function, IP address

ALB bisa route to multiple target groups, health check berada di target group level.
ALB - routing tables to different target groups : 
- based on path in URL, example : example.com/users & example.com/home)
- based hostname in URL, example : one.example.com & other.example.com
- based on query string,headers, example : example.com/users?id=123&order=false


#### NLB 
adalah load balance layer 4 digunakan untuk Meneruskan lalu lintas TCP & UDP ke instance. Handle millions of request per seconds. NLB has one static IP per AZ, and supports assigning Elastic IP

#### GLB 
Deploy, scale, and manage a fleet of 3rd party network virtual appliances in AWS,
> Example: Firewalls, Intrusion Detection and Prevention Systems, Deep Packet Inspection Systems, payload manipulation

Operates at Layer 3 (Network Layer) – IP Packets, Uses the GENEVE protocol on port 6081

<b>Sticky Sessions</b> memungkinkan untuk implement stickiness sehingga klien yang sama selalu dialihkan ke instance yang sama di belakang load balancer.
berfungsi untuk Classic Load Balancer, Application Load Balancer, dan Network Load Balancer. stickiness mungkin membuat imbalance pada load balancer.
For both CLB & ALB, the “cookie” used for stickiness has an expiration date you control
> Use case: make sure the user doesn’t lose his session data

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/32c7071b-e028-45c6-b433-ab115522443f)
> Cross-Zone Load Balancing adalah mendistribusikan semua instance yang terdaftar di AZ secara merata.
> Without Cross Zone Load Balancing adalah mendistribusikan instance yang berada di node ELB
Cross-Zone Load Balancing 
- Application Load Balancer
  - Enabled by default (can be disabled at the Target Group level) 
  - No charges for inter AZ data 
- Network Load Balancer & Gateway Load Balancer 
  - Disabled by default 
  - You pay charges ($) for inter AZ data if enabled 
- Classic Load Balancer 
  - Disabled by default 
  - No charges for inter AZ data if enabled
 
#### SSL/TLS
SSL mengijinkan traffic antara client dan load balancer to be encrypted in transit (in-flight encryption).
- SSL refers to Secure Sockets Layer, used to encrypt connections 
- TLS refers to Transport Layer Security, which is a newer version

<b>SNI</b> solves the problem of loading multiple SSL certificates onto one web server (to serve multiple websites). protokol yang lebih baru dan mengharuskan klien untuk menunjukkan nama host server target di initial SSL handshake.

<b>Connection Draining</b> is Time to complete “in-flight requests” while the instance is de-registering or unhealthy.
ketika client terhubung dengan salah satu server yang ternyata dalam keadaan draining maka diberi waktu yang cukup untuk menyelesaikan koneksi yang ada.kertika semuanya selesai maka koneksi akan dimatikan dan ketika client meng-akses ALB maka akan diarahkan ke server yang baru.

### ASG
> scale out : add EC2 instance agar sesuai dengan increased load
> scale in : remove EC2 instance agar sesuai dengan decreased load

pastikan mempunyai minimum instance yang dijalankan dan maksimum instance yang tersedia.secara otomatis register new instance ke load balancer. 
jika instance unhealthy maka ASG akan re-create EC2 sebelum diterminated.
<b>ASG are free!!</b>
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/68a863a9-e903-4bfa-acfb-10c2b68f5d3a)

#### ASG - Cloudwatch
mengskalakan melalui cloudwatch alamr, alarm monitor metric (average cpu, custom metric)
based on the alarm : 
- We can create scale-out policies (increase the number of instances)
- We can create scale-in policies (decrease the number of instances)

Dynamic Scaling Policies :
- Target Tracking : Most simple and easy to set-up, ex : average ASG CPU to stay at around 40%
- Simple / Step Scaling : CloudWatch alarm is triggered (example CPU > 70%), then add 2 units
- Scheduled Actions : Anticipate a scaling based on known usage patterns, ex :  increase the min capacity to 10 at 5 pm on Fridays

Good metrics to scale on : 
- cpu utilization : : Average CPU utilization across your instances
- request count per target : make sure jumlah request per EC2 is stable
- average network in/out : application is network bound
- any costum metric :  push using CloudWatch

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1746757806353793484)

