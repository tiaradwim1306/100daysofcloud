# New post title here

## Introduction


## Cloud Research
## ELB (Elastic Load Balancing)

### launch instances
- launch first instance
![image](https://user-images.githubusercontent.com/120786669/224482746-b0bf6289-a0d8-4f78-82ef-0e3f97711697.png)

- user data for first instance 
![image](https://user-images.githubusercontent.com/120786669/224482772-105b26a3-e4ff-4af2-a806-13faf982bc40.png)

- launch second instance 
![image](https://user-images.githubusercontent.com/120786669/224482800-620f6740-4679-4b78-bcf3-6329a814d617.png)

- create with a different user data
![image](https://user-images.githubusercontent.com/120786669/224482828-c4aebf82-a267-4fc0-b48d-5151379d6849.png)

- and finally,we have 2 instances
![image](https://user-images.githubusercontent.com/120786669/224482877-9c2c77e4-6828-4c89-b7e3-e1a115e2fb75.png)

### create load balancer 

- go to load balancer tab and click create load balancer 
![image](https://user-images.githubusercontent.com/120786669/224482988-e72aadb9-0d28-407e-9181-4f1ff61cd802.png)

- choose application load balancer and klik create 
![image](https://user-images.githubusercontent.com/120786669/224483075-ab4e7087-8ccd-457b-a7c8-b9ef5fc80ed7.png)

- give it name and leave as default 
 ![image](https://user-images.githubusercontent.com/120786669/224483055-45b49ada-fac6-4c5c-93ff-d3eea6897f0b.png)

- select all AZ 
![image](https://user-images.githubusercontent.com/120786669/224483124-2534cad8-9c41-41ee-bdf0-ffa93015d2e2.png)
![image](https://user-images.githubusercontent.com/120786669/224483130-1103b42f-3a96-43a9-b7be-e4c2101b3b80.png)

- the security group is made the same as the instance's security group
![image](https://user-images.githubusercontent.com/120786669/224483214-9037bfc2-8981-40af-a270-6c604086f609.png)

- click create target group
![image](https://user-images.githubusercontent.com/120786669/224483223-897374c4-d3df-4b45-844f-65b844b4708c.png)

- on basic configuration, choose instance and give it name for target group
![image](https://user-images.githubusercontent.com/120786669/224483348-31511af9-9b82-4c74-a313-dd535caeca22.png)

- scroll and click next
![image](https://user-images.githubusercontent.com/120786669/224483350-6dafeeac-3fc9-45cf-a4b3-b02ab1b6de89.png)

- select the instance we will insert into the ELB,click include as pending below
![image](https://user-images.githubusercontent.com/120786669/224483425-94a321c1-f1cc-4e15-a9c0-e186a5cae954.png)

- return to the ELB build session and choose target that have been created
![image](https://user-images.githubusercontent.com/120786669/224483482-34136790-5ad2-4d12-a438-7e695356452f.png)
 
 - scroll and review summary,click create load balancer 
 ![image](https://user-images.githubusercontent.com/120786669/224483555-678c8f58-d799-43ff-8c88-28d6338a713a.png)

- go to target group tab and choose ALB and review that the instance has been added
![image](https://user-images.githubusercontent.com/120786669/224483673-28846245-0f7e-4048-a9e2-21c1ef9e8e7a.png)

- go to load balancer tab and copy dns name 
![image](https://user-images.githubusercontent.com/120786669/224483686-13debc17-310b-4c37-bafc-484971a01549.png)

- access web server
![image](https://user-images.githubusercontent.com/120786669/224483704-4a30eab2-1a3c-421e-a39a-9d96a6ac5a04.png)

- when refreshed the web server will change to the second server
![image](https://user-images.githubusercontent.com/120786669/224483741-da8b0989-f533-42f7-9922-456964a355bf.png)






## Social Proof

✍️ Show that you shared your process on Twitter or LinkedIn

[link](link)
