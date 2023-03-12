# Meet 7 | ELB & ASG hands on (mentor : yosep kusuma wibawa)

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
![image](https://user-images.githubusercontent.com/120786669/224519192-3f98d9e6-1065-4a24-92f6-f2d3df18c372.png)

- scroll and click next
![image](https://user-images.githubusercontent.com/120786669/224519211-9956f573-a0ef-4f50-bc94-fd2b419ff537.png)


- select the instance we will insert into the ELB,click include as pending below, and click create target group
![image](https://user-images.githubusercontent.com/120786669/224483425-94a321c1-f1cc-4e15-a9c0-e186a5cae954.png)

- return to the ELB build session and choose target that have been created
![image](https://user-images.githubusercontent.com/120786669/224483482-34136790-5ad2-4d12-a438-7e695356452f.png)
 
 - scroll and review summary,click create load balancer 
 ![image](https://user-images.githubusercontent.com/120786669/224483555-678c8f58-d799-43ff-8c88-28d6338a713a.png)

- go to target group tab and choose ALB and review that the instance has been added
![image](https://user-images.githubusercontent.com/120786669/224483673-28846245-0f7e-4048-a9e2-21c1ef9e8e7a.png)

- go to load balancer tab and copy dns name 
![image](https://user-images.githubusercontent.com/120786669/224483686-13debc17-310b-4c37-bafc-484971a01549.png)

### verify
- access web server
![image](https://user-images.githubusercontent.com/120786669/224483704-4a30eab2-1a3c-421e-a39a-9d96a6ac5a04.png)

- when refreshed the web server will change to the second server
![image](https://user-images.githubusercontent.com/120786669/224483741-da8b0989-f533-42f7-9922-456964a355bf.png)


## ASG (Auto Scaling Group)

### create ASG 
- go to Auto scaling group tab and click create auto scaling group 
![image](https://user-images.githubusercontent.com/120786669/224518292-0284fe3f-a1c2-46b1-8825-0fbde9cc57f8.png)

- give it name for auto scaling name
![image](https://user-images.githubusercontent.com/120786669/224518322-8453e9a7-ecd7-4d01-9002-92626097a666.png)

- cause we dont have template click create launch template
![image](https://user-images.githubusercontent.com/120786669/224518325-6ebb0960-a022-45ea-894e-8ff121829b1d.png)

- give it name for template,configuration as usual
![image](https://user-images.githubusercontent.com/120786669/224518335-01f8ea05-cf34-4c88-96e3-2fd949604be3.png)

- review summary and click launch template
![image](https://user-images.githubusercontent.com/120786669/224518433-34707491-d412-4aaf-9df2-ea4143df47f1.png)

- return to the ASG creation page and select the template we have created,click next
![image](https://user-images.githubusercontent.com/120786669/224518484-bad32993-259c-41e3-b4f2-c206122004be.png)

- review and click next
![image](https://user-images.githubusercontent.com/120786669/224518506-646457ac-776c-42d5-b63a-c8e5dd46a160.png)

- edit network settings and select the same VPC as the VPC instance, select the AZ you want to launch your EC2 template
![image](https://user-images.githubusercontent.com/120786669/224518571-9d041493-9667-45df-8471-cb81f4b47c2a.png)

- scroll and review,click next
![image](https://user-images.githubusercontent.com/120786669/224518584-673cbbd7-09f1-4c68-b7af-9211e71535a0.png)

- attach to existing load balancer and choose target ALB
![image](https://user-images.githubusercontent.com/120786669/224518615-b99145c3-1754-4cca-8008-de390d12d30f.png)

- check list ELB dan enter time to check healthy,click next
![image](https://user-images.githubusercontent.com/120786669/224518657-5d933bd8-22a7-489c-87f7-bcd4fb90b878.png)

- enter desired,min,and max capacity for launch instances
![image](https://user-images.githubusercontent.com/120786669/224518715-fef32c1a-1aa9-49eb-9dae-0b2ccc03924f.png)

- leave it as default and next
![image](https://user-images.githubusercontent.com/120786669/224518722-dddec0b3-960f-41f2-aeae-13181aa67f19.png)

- leave it as default and next
![image](https://user-images.githubusercontent.com/120786669/224518729-fd38a306-d2a6-4c7b-a94b-1970f713c2f5.png)

- leave it as default and next
![image](https://user-images.githubusercontent.com/120786669/224518740-22656eed-b47e-4340-96d5-b7b0e08a8f43.png)

- finally,scroll and click create auto scaling group
![image](https://user-images.githubusercontent.com/120786669/224518752-200c0ab5-6953-435d-9782-bf481447c36a.png)

### verify
- there will be 2 instances created automatically
![image](https://user-images.githubusercontent.com/120786669/224518794-b721c2f1-4cb0-4282-a1bb-a84dd75c3a3b.png)

- we can check the activity tab in ASG
![image](https://user-images.githubusercontent.com/120786669/224518837-d14e9c4d-a293-45ec-b625-bcd22d91ce66.png)

- when we terminated one instance,then 1 new instance will appear because we have 2 desired capacity
![image](https://user-images.githubusercontent.com/120786669/224518839-04895741-8c00-4b6e-9e7f-cc5df4f150bb.png)

- and in the activity tab a new notification will appear that successfully launched 1 instance
![image](https://user-images.githubusercontent.com/120786669/224518896-09a18539-e2c4-44fc-a44d-97f99428c42c.png)

- and when we terminated all instances, 2 new instances will appear due to the desired capacity that we have set
![image](https://user-images.githubusercontent.com/120786669/224518929-6bce029f-b200-4655-a088-cb76fa75c857.png)


## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1634731119705993217)
