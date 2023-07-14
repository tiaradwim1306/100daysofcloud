# EFS hands on

## Cloud Research
on this journey we practice EFS hands on,with steps like :
1. create sg for EFS
2. create EFS
3. mount file system to first instance
4. mount file system to second instance with different AZ


### create security groups
- search EC2 and go to security groups tab
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/b41ad89d-2819-4cf0-8d9c-4a5780592fdb)

- give it name and details,choose the vpc
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/a76dc746-0780-4f04-8ffe-489abcb89ae8)

- choose type is NFS and source anywhere IPv4,scroll and click create security groups
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/083523d3-6392-437c-a74e-9750235faa22)

### create File System / EFS
- search EFS
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/f2b1fa13-3345-4d20-8f14-90f86624c60c)

- click create file system 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/7e77e3ac-028d-454a-a6b8-73431b2e525f)

- click customize 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/0a74be9c-8d57-4391-88c4-686abff0777d)

- give it name,choose standart if you need for multiple AZ and one zone for single AZ
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/4b5264b5-4097-450f-b666-c6a7cd11d3bb)

- choose bursting and general purpose,click next
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/32acc4f2-9c8a-4f5a-a93a-0c044d03643f)

- choose VPC and remove AZ and leave only us-east-1a and change the sg to the sg we have created
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/18ab577e-83b8-40b3-b18f-4ac77b968e2e)

- leave it as default and click next  
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/8518a6a8-6a6d-42db-95ea-41ae8ca20388)

- review 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1c162d01-bfef-4444-9400-4f917d27b270)

- scroll and click create
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/566d3059-47d1-45a2-a1f6-058b7acfc411)

- click your EFS on tab network
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/daba862a-54fc-45c7-b1e1-24fbb9b4b6b4)

- prepare 2 instances which will be used to mount the file system that we have created
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/788d18ab-8d70-44dc-8cfc-98fba9fafc74)

### mount the file system in us-east-1a 
- select the web-server1 instance that uses the availability zone us-east-1a and click connect,then click connect
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/e23ef139-4f62-4fee-a8ef-bfe7ab081cd0)

- return to EFS tab and click attach
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1a2861b0-6fad-4d3b-bd11-aefa68b06267)

- copy command for mount 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/7ba27655-8e45-4ec6-b1e2-9114af30d2fc)

- switch to your instance cli,go to root and install amazon-efs-utils
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/4f21384a-b924-4a2e-a292-9de3d6ca2809)

- create directory /efs,and paste the command with change the last command to the directory you have created
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/f1600d3f-da49-4c33-88e4-da57bfaf6c79)

- check with the command df -h, whether the file system that we created has been added or not
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/49b99d23-7c9b-4874-ab44-d7ca37bbb067)

### mount the file system in us-east-1b
- switch to EFS tab,in tab network click manage
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/9fe1014d-8349-45d1-9528-8a4116890960)

- click add mount target,choose us-east-1b and choose sg we have created then click save
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/6aa0d646-58b1-49bf-8d1f-aea14193a168)

- review in tab network we have 2 AZ,so the file system can be mount to us-east-1a or us-east-1b
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/268dbf14-108e-443b-b0ed-8775f6bf3f54)

- choose web-server2 and click connect,review then click connect
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/a6de2dae-861e-4516-a2a2-1851db6200b4)

- same as before we have to go to root and install amazon-efs-utils then create /efs directory and mount file system with previous command,and verify with command f -h 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/88f6a6a7-68c8-4f4a-a5b7-a38740447896)
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/6159c316-32c8-4308-a67c-4c37cb28a809)

#### AND FINALLY WE SUCCESSFULLY MOUNT FILE SYSTEM IN INSTANCE WITH DIFFERENT AZ

## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1679667409173770240)
