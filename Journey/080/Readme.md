# IAM : AWS Certified Solutions Architect Associate SAA-C03 Course on Udemy by Stepahane Mareek

## Cloud Research
### Users & Groups
IAM = Identity and Access Management → Global Service
root account terbuat secara default, jangan digunakan ataupun dishare
<b>users</b> mewakili satu orang yang ada di organisasi tersebut dan bisa dimasukan kesebuah grup

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/a93e59b9-4e7e-4990-bc9b-19ca8e8d7ed3)

<b>group</b> hanya berisi user dan bukan grup lain, user tidak harus mempunyai grub, dan satu user bisa memiliki multiple groups.

### IAM : permissions 
- user atau grub bisa menetapkan JSON document yang disevut policies
- policies ini membantu menentukan permission sebuah user
- prinsip ‘least privilege principle’ jangan berikan permission lebih dari apa yang dibutuhkan user tersebut.

#### IAM structure : 
- version : policy language version
- id : identifier for the policy (optional)
- statement : statemnt bisa lebih dari satu (wajib), statement berisi beberapa hal :
	- Sid : identifier for statement (optional)
	- Effect : allow or denies access
	- principal : account/user/role yang akan diberikan permissions
	- action : actions yang diallows atau didenies
	- resource : resource tempat action akan diterapkan
	- conditions : kapan berlakunya (optional)


#### IAM Password Policy : 
- strong password
- setup password policy (uppercase, lettercase,numer,non-alphanumeric character)
- allow IAM user change password mereka sendiri
- require user to change password setelah beberapa waktu (password expiration)
- melarang password re-use


### MFA (Multi Factor Authentication)
MFA adalah security device yang bisa berupa virtual atapun hardware, benefitnya adalah ketika sandi dicuri dan dihacked maka akun tetap tidak bisa dibobol karena memerlukan code MFA
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/c4e47d17-50bd-4ea4-8de1-386dfb409a2d)
#### Access AWS :
- cosole (protect by password + MFA)
- CLI (protect by access key)
- SDK (protect by access key)

<b>Access key are secret like password, dont share them!!</b>
> - access key ID = username
> - Secret Access Key = password

- <b>AWS CLI</b> memungkinkan interact with AWS dengan command di command-line shell, mengembangkan skrip untuk mengelola resource dan open source.
- <b>AWS SDK</b> mengakses dan mengelola service AWS secara terprogram, support : 
SDKs (JavaScript, Python, PHP, .NET, Ruby, Java, Go, Node.js, C++), Mobile SDKs (Android, iOS, …), IoT Device SDKs (Embedded C, Arduino, …)
example : AWS CLI built on SDK for python

### IAM Roles
memberikan permission kepada aws service ke other AWS service using IAM Roles.
common rules : EC2 instance roles, lambda function roles, roles for cloudformation


### IAM best practice : 
- jangan gunakan user root selain digunakan untuk setting users
- satu orang satu user
- masukan user ke group dan tetepkan izin group
- buat strong password policy
- use MFA
- create roles untuk memberikan permissions ke aws services
- use acces keys untuk programmatic access (CLI / SDK)
- audit permissions dengan IAM credential report & IAM access advisor
- jangan pernah share IAM & access keys secara sembaranagan

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1746744173892628729)






