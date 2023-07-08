# EFS hands on

## Cloud Research
### create security groups
- search EC2 and go to security groups tab
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/b41ad89d-2819-4cf0-8d9c-4a5780592fdb)

- give it name and details,choose the vpc
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/a76dc746-0780-4f04-8ffe-489abcb89ae8)

- choose type is NFS and source anywhere IPv4,scroll and click create security groups
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/083523d3-6392-437c-a74e-9750235faa22)

### create security groups
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

- leave it as default and click nest  
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/8518a6a8-6a6d-42db-95ea-41ae8ca20388)

- review 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1c162d01-bfef-4444-9400-4f917d27b270)

- scroll and click create
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/566d3059-47d1-45a2-a1f6-058b7acfc411)

- click your EFS on tab network
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/daba862a-54fc-45c7-b1e1-24fbb9b4b6b4)

- prepare 2 instances which will be used to mount the file system that we have created
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/788d18ab-8d70-44dc-8cfc-98fba9fafc74)

- choose web-server1 and click connect,then click connect
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/e23ef139-4f62-4fee-a8ef-bfe7ab081cd0)

- return to EFS tab and click attach
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/1a2861b0-6fad-4d3b-bd11-aefa68b06267)

- copy command for mount 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/7ba27655-8e45-4ec6-b1e2-9114af30d2fc)





## Social Proof

✍️ Show that you shared your process on Twitter or LinkedIn

[link](link)
