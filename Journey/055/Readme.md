# Meet 10 | computing,network,alert (mentor : Dea Tristianti)

## Introduction
on this journey we will learn with easy stack, easy stack is a cloud platform with open stack based. easy stack is a hybrid cloud service in Asia.
steps taken:
- upload image
- create network and subnet
- create instance
- create SSH key pair
- create alert 

## Cloud Research
### apload image
- click service catalog and choose instance image
![image](https://user-images.githubusercontent.com/120786669/235561161-3ea88a71-5a9f-447e-98a5-60bbde66d59a.png)

- click create image
![image](https://user-images.githubusercontent.com/120786669/235561839-4bb4f09a-1e48-44ad-a936-24861a8534c7.png)

- givw it name,on image source click aploud file and select the file you want to upload
![image](https://user-images.githubusercontent.com/120786669/235561849-ed6b8272-cfa7-4c61-b396-ac575678bd41.png)

- fill in the required information then click Create
![image](https://user-images.githubusercontent.com/120786669/235561957-11174810-6335-48b6-8e87-47b2f5d2baca.png)

### Create network & subnets
#### create network 
- click service catalog and choose network 
![image](https://user-images.githubusercontent.com/120786669/235562482-e30b95ca-2e6e-4f39-b8a5-b9864b8706b1.png)

- click create network 
![image](https://user-images.githubusercontent.com/120786669/235562734-2d46b399-165c-492c-9cd7-ea0a62e36641.png)

- give it name,and enter your IPV4 CIDR,there are 3 recommended internal netork segmen : 10.0.0.0/8-29,172.16.0.0/12-29,192.168.0.0/16-29
![image](https://user-images.githubusercontent.com/120786669/235562760-6b02d396-a704-40b5-b635-0080e285290c.png)

- click advance configuration,enter DNS server and enter your address pool ranges.click create network 
![image](https://user-images.githubusercontent.com/120786669/235563070-445dd011-8855-4ddb-8239-4c3b4841bc93.png)

#### create subnet
actually the subnet was created when we made the network, but this time we will show you how to create a subnet
- go to subnet tab,and click create subnet
![image](https://user-images.githubusercontent.com/120786669/235563506-9c331e05-6d0a-402c-a2eb-0388230e72cf.png)

- select network that was made earlier
![image](https://user-images.githubusercontent.com/120786669/235563597-b4d1a8b9-661d-42ce-9aa8-bb10627f9fd4.png)

- click advanced configuration,enter DHCP server and address pool range.click create subnet
![image](https://user-images.githubusercontent.com/120786669/235563628-2401c7b7-39fd-430e-b637-70b31b0b2b3f.png)

### create instance 
- go to service catalog and choose instance 
![image](https://user-images.githubusercontent.com/120786669/235563744-9e89f350-ebf1-4852-bf0d-7ca762bc1588.png)

- click create instance 
![image](https://user-images.githubusercontent.com/120786669/235563758-566b869b-5224-4832-9340-8ff2f4e7230b.png)

- select image you needed  
![image](https://user-images.githubusercontent.com/120786669/235563897-a64f2eb4-044f-4ad6-b9bb-e16b46201a7a.png)

- then choose how much capacity you need
![image](https://user-images.githubusercontent.com/120786669/235564212-09e66d0f-7f98-4118-a99f-947eed5b2fef.png)

- check delete with instance and click next...
![image](https://user-images.githubusercontent.com/120786669/235564236-5d82abaf-a5af-40f5-9c2b-f4f9c8fad62a.png)

- select network & subnet that we created earlier,click next
![image](https://user-images.githubusercontent.com/120786669/235564661-9949b222-556c-481b-9842-efc1e5122e25.png)

- give it name for instance,we need key pair
![image](https://user-images.githubusercontent.com/120786669/235564814-986c68e1-af65-41a2-8afa-18ab1e96ea3c.png)

### create SSH key pair
- for that, duplicate tab and choose SSH key pair in service catalog
![image](https://user-images.githubusercontent.com/120786669/235564968-a0b2fe2b-3173-4ec2-9667-fde18603e63f.png)

- click create key pair
![image](https://user-images.githubusercontent.com/120786669/235565014-9f7f410c-2f7d-4557-b22c-6d5b70c8be08.png)

- give name for your key pair,click create
![image](https://user-images.githubusercontent.com/120786669/235565538-d5ce7369-e150-4efb-962b-0867aa6b1439.png)

- copy public key and save in your computer/laptop
![image](https://user-images.githubusercontent.com/120786669/235565611-8370d862-1002-4428-91ea-c63ae015de97.png)

- back to create instance tab,and click key pair you made earlier. click confirm
![image](https://user-images.githubusercontent.com/120786669/235565631-916cfdae-daee-4b79-b333-f97481bd136d.png)

- review and click create instance
![image](https://user-images.githubusercontent.com/120786669/235565873-d2741550-d0ea-4898-8f4a-25cff593aa3e.png)

- and finally we success create instance,wait until the instance status becomes active
![image](https://user-images.githubusercontent.com/120786669/235566105-2fa1ae8c-9c35-4727-a32a-63d0e433abbb.png)

### create alert 
#### create alert
- choose alert management in service catalog 
 ![image](https://user-images.githubusercontent.com/120786669/235566519-4cb098c9-c4f2-4a2f-8584-083c8c2b3d02.png)

- click create alert
![image](https://user-images.githubusercontent.com/120786669/235566502-d1756c0d-a120-4f4b-9f32-6e8a9be6a834.png)

- choose instance we made earlier,click next
![image](https://user-images.githubusercontent.com/120786669/235566633-36ae6dc5-131c-4615-aa20-a4c092fad6ba.png)

- give it name, example here is test.then enter your periodic and click automatically fill in the description.then a description will appear according to the periodic that has been selected.click next
![image](https://user-images.githubusercontent.com/120786669/235566966-36ee9574-583d-48cd-9d84-bdd56e9856a5.png)

- then set your notification
![image](https://user-images.githubusercontent.com/120786669/235567075-cc3de5a4-f0b8-4320-9f6f-51f08abc7d2d.png)

#### edit alert
- select alert and click edit to change the name,description, monitoring threshold, and notification list of the monitoring resource.
![image](https://user-images.githubusercontent.com/120786669/235567361-96379280-dc9b-4b67-ae40-c076b4ba1a48.png)

- you can change name and periodic,then click next
![image](https://user-images.githubusercontent.com/120786669/235567400-bca47e9c-f766-4b42-aa64-f7ac6590af29.png)

- On the page for selecting a notification list, select an option from Normal, Alert, and Insufficient data for Resource Status, and select an option for Notification Object. You can also create or update a notification list. After all modifications are completed, click Save to complete the Alert editing operations.
![image](https://user-images.githubusercontent.com/120786669/235567865-66194925-ad77-467b-a64a-d85545194688.png)

#### delete alert
- choose your alert then click delete alert
![image](https://user-images.githubusercontent.com/120786669/235567914-ef72818c-b42d-4bb4-8103-41aff1cc186b.png)

- click delete alert
![image](https://user-images.githubusercontent.com/120786669/235567985-a9d50708-cc43-4bfb-bfc0-254301de9118.png)

### shutoff instance 
- select instance and click shutoff
![image](https://user-images.githubusercontent.com/120786669/235568857-89933766-5788-43c0-ad9c-19c2873c3ee3.png)

- click shutoff
![image](https://user-images.githubusercontent.com/120786669/235568878-9a5903ff-5122-4056-b121-61b62e7f8b30.png)

### check activity 
- click operational audit
![image](https://user-images.githubusercontent.com/120786669/235568782-cb6725da-715e-455a-84e5-4d70d9d834b0.png)


## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1653234131843846144)
