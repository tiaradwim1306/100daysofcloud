# CloudFront & Global Accelerator: AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
### Amazon CloudFront 
adalah Content Delivery Network (CDN) yang improves read performance dengan menyimpan content is cached at the edge.Improves users experience and has 216 Point of Presence globally.
> DDoS protection cause integration with Shield, AWS Web Application Firewall.

- S3 : Untuk mendistribusikan file dan menyimpannya di edge, security with CloudFront Origin Access Control (OAC), CloudFront dapat digunakan sebagai ingress (untuk mengunggah file ke S3)
- Custom Origin (HTTP) : ALB,EC2 instance, S3 website, any HTTP backend you want.

ketika client melakukan request maka edge akan mengecek apakah cache memilikinya jika tidak maka edge akan mengambil ke server dan menyimpannya kedalam cache.
nanti jika client melakukan request yang sama edge tidak perlu keserver lagi dan bisa mengambilnya cache.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/fd40acb8-ed7b-44ab-903e-49d79c8425e9)

#### CloudFront Geo Restriction
- allowlist : Izinkan pengguna Anda mengakses konten Anda hanya jika mereka berada di salah satu negara dalam daftar negara yang disetujui.
- blocklist : Mencegah pengguna mengakses konten Anda jika mereka berada di salah satu negara dalam daftar negara yang dilarang.

The “country” ditentukan menggunakan database Geo-IP pihak ketiga, Use case: Copyright Laws to control access to content. CloudFront Edge locations are all around the world, The cost of data out per edge location varies.

#### Cache Invalidations
jika memperbarui backend origin CloudFront tidak mengetahuinya dan hanya akan mendapatkan konten yang disegarkan setelah TTL kedaluwarsa untuk itu kita harus memaksa penyegaran cache seluruh atau sebagian dengan melakukan CloudFront Invalidation.You can invalidate all files (*) or a special path (/images/*)

- Unicast IP: one server holds one IP address 
- Anycast IP: all servers hold the same IP address and the client is routed to the nearest one

#### AWS Global Accelerator 
work with elastic IP, ec2, ALB, NLB, public or private
- Kinerja yang konsisten : perutean yang cerdas dan failover regional yg cepat, No issue with client cache (because the IP doesn’t change), Internal AWS network
- Health check : help make your application global (failover less than 1 minute for unhealthy), Great for disaster recovery
- Security : only 2 external IP need to be whitelisted,DDoS protection with AWS Shield

#### AWS Global Accelerator vs CloudFront
keduanya sama untuk AWS global network dan edge locations around the world dan sama-sama terintegrasi dengan AWS shield for DDoS  protection,
- CloudFront
  - Meningkatkan kinerja untuk konten yang dapat di-cache (seperti gambar dan video)
  - dynamic content (seperti akselerasi API dan pengiriman situs dinamis)
  - Konten disajikan di edge
- Global Accelerator
  - Meningkatkan kinerja untuk berbagai aplikasi melalui TCP atau UDP
  - Memproxy paket di edge ke aplikasi yang berjalan di satu atau lebih Wilayah AWS.
  - Cocok untuk kasus penggunaan non-HTTP, seperti game (UDP), IoT (MQTT), atau Voice over IP
  - Baik untuk kasus penggunaan HTTP yang memerlukan alamat IP statis
  - Cocok untuk kasus penggunaan HTTP yang memerlukan failover regional yang cepat dan deterministik

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1746790840083812449)
