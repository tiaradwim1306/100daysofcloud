
# meet 4 | IAM hands on

## Introduction
root user is a very dangerous user if used frequently, it would be better if we use a user with certain access rights.
the fewer permissions given, the more secure it becomes.
for that in this lab we will learn IAM hands on to create users and grub and add users to groups.

## cloudResearch
### Scenario : 
![WhatsApp Image 2023-02-24 at 16 14 30](https://user-images.githubusercontent.com/120786669/221415787-d20b614c-3290-44f3-b8c0-6c5a66656a0a.jpeg)

- user1 : policy - S3 Monitoring and Group - VPC Monitoring
- user2 : Group - EC2 Monitoring
- user3 : Group - EC2 Monitoring and VPC Monitoring


## Create Group 
- search IAM and click IAM 
![image](https://user-images.githubusercontent.com/120786669/221415118-f9ed94e2-c3ac-43d9-aca5-0fc605160285.png)

### Create Group - EC2 Monitoring
- go to User groups tab and click create user
![image](https://user-images.githubusercontent.com/120786669/221416164-6c92b4ca-b62f-4760-b31c-9fe78b2db59c.png)

- enter the name of the group
![image](https://user-images.githubusercontent.com/120786669/221416236-973cdc22-1c1e-46c9-ae4f-f7e6e4cb47cf.png)

- scroll and select the policy you want to apply,click create group
![image](https://user-images.githubusercontent.com/120786669/221416344-d77946eb-6e40-4e81-b1d4-0123f860e4e2.png)

### Create Group - VPC Monitoring 
- click create user, and enter the name of the group
![image](https://user-images.githubusercontent.com/120786669/221416578-9382760e-2fe0-4018-a5a5-f5ee61a9615d.png)

- attach the policy and click create group
![image](https://user-images.githubusercontent.com/120786669/221416647-fd2e4bdd-eaed-4e17-8b23-5a9b89bb294b.png)

## Create User

### user1 : policy - S3 Monitoring 
- go to Users tab and click add users
![image](https://user-images.githubusercontent.com/120786669/221416766-47041f50-c76e-443f-9fea-67ccda9db2c9.png)

- enter the name and password to be created,click next
![image](https://user-images.githubusercontent.com/120786669/221416837-56180231-a496-418c-9110-b0167b8b55c9.png)

- click attach policies directly and attach what policies you need,next
![image](https://user-images.githubusercontent.com/120786669/221416983-94ee3eaf-83ac-41c5-a367-00ef62d371af.png)

- review and click create user
![image](https://user-images.githubusercontent.com/120786669/221417113-9bb05d4d-9352-4bf4-bcf3-0eadf6ae2a04.png)

### user2 : Group - EC2 Monitoring
- click add users, enter the name and password to be created,click next
![image](https://user-images.githubusercontent.com/120786669/221417223-afa1830a-bd5c-437e-b168-6fe13d988281.png)

- click add user to group and choose group you need,next
![image](https://user-images.githubusercontent.com/120786669/221417326-b4b8effa-4dcc-4d96-84c3-aa798b300a44.png)

- review and click create user
![image](https://user-images.githubusercontent.com/120786669/221417351-c2769b1a-682a-413b-90e7-3f7604f51e96.png)

### user3 : Group - EC2 Monitoring and VPC Monitoring
- click add users, enter the name and password to be created,click next
![image](https://user-images.githubusercontent.com/120786669/221417461-fafa8f5a-c2ae-4419-b2b4-20b444296d43.png)

- click add user to group and choose group you need,next
![image](https://user-images.githubusercontent.com/120786669/221417523-8bb017e2-e97c-4562-9e1a-8cb6acc38f7d.png)

- review and click create user
![image](https://user-images.githubusercontent.com/120786669/221417568-cdbddee3-deb5-4b93-9f10-c31406599a9a.png)

## Add user to group
- click user you need and go to Groups tab and click add user to group
![image](https://user-images.githubusercontent.com/120786669/221419119-21702f15-9781-4add-8552-497f9aa0bf88.png)

- choose group you need and click add user to group(s)
![image](https://user-images.githubusercontent.com/120786669/221419280-b27971b3-ddae-40c3-b4ae-5e6e37944ff8.png)


## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1629864095813095426)
