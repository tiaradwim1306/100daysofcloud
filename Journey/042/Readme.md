
# Meet 5 | EC2 hands on (mentor : yosep kusuma wibawa)

## Introduction
EC2 is the most important part of AWS, knowing EC2 is fundamental to understanding how the Cloud works.So in this journey we will learn to launch ec2 instance, later we will access web server with public ip and access instance via ssh

## Cloud Research
- search EC2 and click EC2 
![image](https://user-images.githubusercontent.com/120786669/222034847-c6ca36ec-5fbe-46c0-b445-aed1a919e695.png)

- go to Instances tab and click launch instance
![image](https://user-images.githubusercontent.com/120786669/222035124-bde95edc-e2a5-4e42-887b-da51baa67c67.png)

- enter the name of instance 
![image](https://user-images.githubusercontent.com/120786669/222035494-b75d32dd-80b8-498d-82ee-e08ad2e51ef6.png)

- select the OS you want, the example here we use Debian with type Debian 11
![image](https://user-images.githubusercontent.com/120786669/222035686-c5c95a7a-f372-4e0e-aa95-1291dcb38ef0.png)

- for instance type choose t2.micro and click create new key pair for create new key
![image](https://user-images.githubusercontent.com/120786669/222044887-f0000748-1665-427a-9d37-680dc7a456d8.png)![image](https://user-images.githubusercontent.com/120786669/222035906-0863f70c-1da7-4fdb-a462-b5be1b09cc39.png)

- then enter the name of key,for type choose RSA and the format is .pem because later we will try to ssh from cmd
![image](https://user-images.githubusercontent.com/120786669/222036232-8a3e6633-d443-43d1-ad83-bdee72b2cf18.png)

- in network setting tab click Edit
![image](https://user-images.githubusercontent.com/120786669/222036301-94ce26cc-d979-436c-916c-d4f04263fbd4.png)

- For vpc, let it be default. For subnets, we can choose the AZ we want, for example here I chose us-east-1e. And don't forget to choose enable on the auto-assign public IP so that we get a public IP directly.
![image](https://user-images.githubusercontent.com/120786669/222036875-c724e458-ab9b-4c8e-b03a-f734912a146b.png)

- in the inbound rule, create 2 rules, the first for SSH and the second for HTTP because later we want to access the web server
![image](https://user-images.githubusercontent.com/120786669/222037630-b4df8125-5dfb-4d88-805a-93adb5847952.png)

- on the configure storage tab, leave it as default
 ![image](https://user-images.githubusercontent.com/120786669/222037837-f64645a9-3418-4e29-9aaa-8a9855e1f98f.png)

- user data is the script that is executed when the instance is started,in the user data below, we create a simple web server. where we try to install apache2 and create a simple script in index.html
![image](https://user-images.githubusercontent.com/120786669/222038647-af868fe9-897b-4bf2-94c9-9b3d7225a7bf.png)

- check summary,if that's right click launch instance
![image](https://user-images.githubusercontent.com/120786669/222038870-6d775b11-133e-477a-bd31-c851b431b939.png)

- wait a few moments until available changes to running
![image](https://user-images.githubusercontent.com/120786669/222038896-e869672a-29ee-418c-9df8-235196231f98.png)

## Testing 
- access the web server with Public IPV4 address or with Public IPV4 DNS
![image](https://user-images.githubusercontent.com/120786669/222039508-95aca0d2-3490-4a8f-882f-23d9cc616473.png)

![image](https://user-images.githubusercontent.com/120786669/222039541-0b820f35-1a22-4f83-8181-d7577880bd5d.png)

![image](https://user-images.githubusercontent.com/120786669/222039558-ef31b8bc-8601-4d7c-a59e-72fef872d75c.png)

- access instance via SSH,by select the instance then click connect
![image](https://user-images.githubusercontent.com/120786669/222039835-c5fe7a68-0d7d-438a-8832-c0fe975ac8bb.png)


- copy example 
![image](https://user-images.githubusercontent.com/120786669/222039860-3a0311d3-210d-45b3-a019-2acb87b0bbda.png)

- open cmd and switch to where you saved the key generated when creating the instance
![image](https://user-images.githubusercontent.com/120786669/222040055-ba3d04a5-4c10-4452-9481-e63f11a4f697.png)

### well done, we have successfully launched the web server with EC2

## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1630785805013876736)
