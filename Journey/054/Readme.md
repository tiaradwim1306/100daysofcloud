# linux and aws combination | EC2 section

## Introduction
In this journey, we will combine the configuration between Linux Ubuntu and AWS. We will create several websites
- simple web : port 82 ( display : "welcome to tiara's web server" )
- cloned web : port 8088 (display : game 2048)
- cloned web : default port and accessed by domain (display : game star-battle)

## Cloud Research
### launch instances 
- click launch instances
![image](https://user-images.githubusercontent.com/120786669/231325232-919b757c-3461-4bd7-8522-4ae74bcd21ab.png)

- give it name
![image](https://user-images.githubusercontent.com/120786669/231325261-60283206-5020-4234-837e-83df305c8c34.png)

- choose ur OS and the type 
![image](https://user-images.githubusercontent.com/120786669/231325434-9cd88aa0-5998-420c-9c6c-8331943adb20.png)

- use the keypair that we created in the previous lab
![image](https://user-images.githubusercontent.com/120786669/231325455-41fefc60-e403-44f8-bff2-c32a70a5d807.png)

- choose vpc,subnet, u need.then use sg that we created in the previous lab
![image](https://user-images.githubusercontent.com/120786669/231325543-ab3fc544-d9e3-4873-87a6-55992018e8f3.png)

- review summary and click launch instance
![image](https://user-images.githubusercontent.com/120786669/231325684-02b82c15-cae8-4100-b076-ff78b313346f.png)

### remote instance 
- open cmd,move where the keypair is stored
![image](https://user-images.githubusercontent.com/120786669/231326053-b3d0c6da-6617-42a4-84e4-066d4e6dd343.png)

- switch to the root user
![image](https://user-images.githubusercontent.com/120786669/231326115-16a52bc2-32b4-4842-b21c-dc8a7e7e2b01.png)

## first website : simple web (port 82)
- install apache2
![image](https://user-images.githubusercontent.com/120786669/231326345-8ab689f0-1b98-4654-b2eb-f14e8b61bc37.png)

- Enter the script in index.html with the echo 
![image](https://user-images.githubusercontent.com/120786669/231326471-9ba21477-90cf-4ba6-b857-5b98e2745bf7.png)

- access web server,and make sure it is accessible.
![image](https://user-images.githubusercontent.com/120786669/231326527-ae1ee849-617d-4134-87dd-271ec4453e8f.png)

- then try to access with port 82, and the web server canot be accessed with port 82
![image](https://user-images.githubusercontent.com/120786669/231327079-239d92bf-d0c1-45cf-9879-721fe56f23db.png)

- move to /etc/apache2/sites-enabled
![image](https://user-images.githubusercontent.com/120786669/231327164-703279d0-80b2-454d-bb01-13604b6bf06c.png)

- cp 000-default.conf to port82.conf,then edit file port82.conf with nano
![image](https://user-images.githubusercontent.com/120786669/231329130-5f21700f-dede-4613-b77f-dd0b9a11abcf.png)

- edit port and add script listen 
![image](https://user-images.githubusercontent.com/120786669/231329319-ab78563a-ce96-4572-9306-7686f3e181ce.png)

- lalu restart apache2
![image](https://user-images.githubusercontent.com/120786669/231329398-d5a6780e-2a72-4a46-b73f-1b9866d825bd.png)

- we need to configure the security group, for that move to aws EC2 then to the security group tab

- 



## Social Proof

[link](link)
