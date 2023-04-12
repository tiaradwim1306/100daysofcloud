

# launch web server with wordpress | EC2 section 

## Introduction

On this journey, we will learn how to launch a web server with WordPress. The configuration is:
- launch instances
- remote instances
- install php
- install mariadb and create database
- install wordpress
- virtualhost
- access web server & install and create a wordpress account
- and finally, verify

## Cloud Research
### launch instances
- go to EC2 and click launch instances 
![image](https://user-images.githubusercontent.com/120786669/231066287-b79ce3e0-7fc0-4dfb-9c10-801e2733c7da.png)

- give it name 
![image](https://user-images.githubusercontent.com/120786669/231066727-c2d31b95-19da-4a15-8e1b-24bbf20b9fcb.png)

- choose OS u need and select type for OS
![image](https://user-images.githubusercontent.com/120786669/231066823-aaf98aeb-9829-43ed-af87-8c74a3453685.png)

- click create key pair, give it name and choose type and the format
![image](https://user-images.githubusercontent.com/120786669/231067055-a267dca3-6a13-4cbd-99b3-31616bb24e08.png)

- choose keypair that was made earlier
![image](https://user-images.githubusercontent.com/120786669/231067177-8acdcd62-7518-4e63-a1c3-3bffb64a90fc.png)

- in network setting section select vpc,subnet u need
- create a security group with ssh and http privileges
![image](https://user-images.githubusercontent.com/120786669/231068684-b0ea0ef6-d861-4e12-b47e-f7d6b95f5aa1.png)
![image](https://user-images.githubusercontent.com/120786669/231068711-379a1102-3afb-45ce-8cc5-44774de00419.png)

- in userdata add a script to install apache2
![image](https://user-images.githubusercontent.com/120786669/231068915-6a82ef70-7d9f-44e9-b9be-ccc198b784a5.png)

- review summary and click launch instances
![image](https://user-images.githubusercontent.com/120786669/231322097-9293403c-3fb4-40a7-8e2a-37a717706e1b.png)

- try to access the webserver
![image](https://user-images.githubusercontent.com/120786669/231069138-12121089-d77f-4cf5-8d43-9402971f9b7f.png)

### remote instances
- remote instances
![image](https://user-images.githubusercontent.com/120786669/231069265-83827cc8-5e06-4938-aa8c-a272e6fe828f.png)

- switch to user root
![image](https://user-images.githubusercontent.com/120786669/231069374-8897f9ba-8fa6-4fe7-b4ae-7e9fdea6b6c3.png)

### install php 
- install php and extension
![image](https://user-images.githubusercontent.com/120786669/231069456-6d957b75-7a16-4047-a660-760fe9dcb241.png)

- integrate php and apache2
![image](https://user-images.githubusercontent.com/120786669/231317450-33891ed4-d481-44bb-a0cb-b70b42e2c4d1.png)

### install mariadb and create database
- install mariadb-server
![image](https://user-images.githubusercontent.com/120786669/231317879-73693168-46b9-4029-a4c3-3b2e6f4c07ab.png)

- create a database, then create a user and give access to the database
![image](https://user-images.githubusercontent.com/120786669/231318276-2a8d83a9-9e9e-4c43-bc93-0e5154f73dfd.png)

### install wordpress (Document Root)
- move to /var/www/,then install wordpress. wordpress available at [klik link](https://wordpress.org/latest.zip)
![image](https://user-images.githubusercontent.com/120786669/231318815-a607aaf0-6a6c-4cac-b77c-7ebe7fa14872.png)

- and unzip package
![image](https://user-images.githubusercontent.com/120786669/231318871-6d5bbbc9-cd39-4539-bb25-33bb2ec51d4d.png)

- change the ownership of the wordpress folder to user and group www-data
![image](https://user-images.githubusercontent.com/120786669/231319015-de528769-efd5-474d-8054-aa6a259f0867.png)

### virtualhost
- move to /etc/apache/sites-enabled/,then edit file 000-default.conf
![image](https://user-images.githubusercontent.com/120786669/231319145-96172321-aa61-49af-9b12-3d9b4b8375b5.png)

- ubah DocumentRoot according to the location of the wordpress folder
![image](https://user-images.githubusercontent.com/120786669/231319284-f082ab88-f3d1-4d9e-9d10-1cf87b2349b3.png)

- copy the file wp-config-sample.php in the wordpress folder to become wp-config.php
![image](https://user-images.githubusercontent.com/120786669/231319781-bdaafd69-d307-46c6-97da-5f6b5e1c5c5e.png)

- edit file wp-config.php
![image](https://user-images.githubusercontent.com/120786669/231319818-581ea11e-5d38-4dcd-b8d3-6520998be047.png)

- adjust according to the database information we have created
![image](https://user-images.githubusercontent.com/120786669/231320011-99ee07c1-75b9-452a-9280-ec8ba82b5fbb.png)

- restart apache2
![image](https://user-images.githubusercontent.com/120786669/231320185-b675da8b-8011-4415-926e-df110fcf3e8a.png)

### access web server & install and create a wordpress account
- access web server with ur ip public,choose english
![image](https://user-images.githubusercontent.com/120786669/231320335-3f383674-6c5d-4284-88bc-17b1cb7ebaf9.png)

- click let's go
![image](https://user-images.githubusercontent.com/120786669/231320338-2ca5ed0a-9b48-47ce-a6d0-bca62f05154e.png)

- enter the database name, user, and password that was created earlier,click submit
![image](https://user-images.githubusercontent.com/120786669/231320769-636d46a8-ba60-41a2-b86f-6a8d67babc8b.png)

- click installing now
![image](https://user-images.githubusercontent.com/120786669/231320820-91316ec8-96db-49a9-b410-9c465b256b80.png)

- enter wordpress account information that you want,click install wordpress
![image](https://user-images.githubusercontent.com/120786669/231320959-102ab997-b602-4125-83e2-663b46996819.png)

- when finished, click login
![image](https://user-images.githubusercontent.com/120786669/231320969-eb9463eb-55bd-4a8f-a117-a2c5733acfc2.png)

- enter username and password u made earlier
![image](https://user-images.githubusercontent.com/120786669/231321065-b7bd712f-0ee1-4fc5-b4a7-de8902ffa31f.png)

### verify
![image](https://user-images.githubusercontent.com/120786669/231321284-e602253b-7d4f-4009-95ed-fa3416405dfb.png)

- access ur public ip 
![image](https://user-images.githubusercontent.com/120786669/231321315-9fa86279-cad4-4646-83c6-7202cbdbb9b6.png)


### good job,web server with wordpress finally succeeded

## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1645961117330706432)
