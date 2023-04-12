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
![image](https://user-images.githubusercontent.com/120786669/231331342-30e876b2-54cc-4d52-bcbb-d01fc0e86258.png)

- click add rule,type : custom tcp,port : 82,src : anywhere. click save rules
![image](https://user-images.githubusercontent.com/120786669/231331667-81211dc0-3f55-4322-8cec-8e86e4764f42.png)

- try again access web server with port 82,and make sure we can access it
![image](https://user-images.githubusercontent.com/120786669/231332440-2f852054-a698-4a84-8efb-4aa5af30137d.png)

## second website : games 2048 (port 8088)
- create RootDocument,move to /var/www.then clone github from [github](https://github.com/gabrielecirulli/2048.git). make sure folder 2048 already exists
![image](https://user-images.githubusercontent.com/120786669/231333259-fc23a5cb-cce1-4d2c-8bcf-fffe794e4777.png)

- move to /etc/apache/sites-enabled, then cp 000-default.conf to games.conf,
 then edit games.conf
![image](https://user-images.githubusercontent.com/120786669/231334610-47d8a06c-051a-4770-a791-8804a8e3fd35.png)

- change port and customize the document root
![image](https://user-images.githubusercontent.com/120786669/231334888-3b01cc6e-50ce-4749-8c18-399b41f72cc1.png)

- restart service
![image](https://user-images.githubusercontent.com/120786669/231335066-787a603b-377c-4aae-b6f4-75c37daa4a55.png)

- go to security groups tab,click edit inbound rules
![image](https://user-images.githubusercontent.com/120786669/231335266-bc189ce8-63a8-4da8-8ae9-7febb9a3a5e0.png)

- click add rule,type : custom tcp,port : 8088,src : anywhere.click save rules
![image](https://user-images.githubusercontent.com/120786669/231335278-3ffd954f-1f33-4c81-8dbd-5eaf4c7a27ca.png)

- verify with access ur ip public with port 8088
![image](https://user-images.githubusercontent.com/120786669/231335544-a4d9966c-c45b-46a1-ad3e-19119889c036.png)

## third website : games star-battle (domain)
- create virtual host first, copy 000-default.conf to games2.conf.edit games2.conf
![image](https://user-images.githubusercontent.com/120786669/231336627-26525d54-54ad-4345-8123-fa391cfc4b15.png)

- port leave it as default,and customize DocumentRoot
![image](https://user-images.githubusercontent.com/120786669/231337619-90ecfa34-2db4-44e3-84c7-1b62621e4c7d.png)

- create RootDocument,move to /var/www.then clone github from [github](https://github.com/gd4Ark/star-battle.git). make sure folder 2048 already exists
![image](https://user-images.githubusercontent.com/120786669/231338670-8283f203-b265-4a52-aa68-301fc611c6d2.png)

- restart service
![image](https://user-images.githubusercontent.com/120786669/231338694-5aeeaeeb-34b6-4c19-8ac5-4845e65f4a63.png)

- verify, access ip public
![image](https://user-images.githubusercontent.com/120786669/231339301-869c5b79-ee8f-40a7-bb4f-c99e4357232f.png)


### configure domain  
- move /etc/apache2/sites-enabled, edit games2.conf
![image](https://user-images.githubusercontent.com/120786669/231339012-4733553a-0e06-4748-a65e-822bca3f9498.png)

- add ServerName, domains can be registered using Route 53 on AWS
![image](https://user-images.githubusercontent.com/120786669/231339100-93f64b3f-b2fe-4adf-8198-19c160eed4c6.png)

- access web server with ur domain, click click here
![image](https://user-images.githubusercontent.com/120786669/231339323-261c65bf-9e52-45b9-8033-b6adcee708ce.png)

- have fun,with this game <3
![image](https://user-images.githubusercontent.com/120786669/231339400-66737b84-cef0-434e-a875-2f0035935de6.png)

### it's also exciting to combine between linux and aws.

## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1645992682274320385)
