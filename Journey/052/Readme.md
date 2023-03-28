
# Meet 8 | VPC hands on (mentor : yosep kusuma wibawa)

## Cloud Research
## Create VPC and subnets

- search VPC and click VPC
![image](https://user-images.githubusercontent.com/120786669/228117242-72b2d3ab-0aa4-4b63-b296-43e675218c00.png)

### Create VPC
- go to your VPCs tab and click create VPC
![image](https://user-images.githubusercontent.com/120786669/228117428-c98651dc-4ce5-46ac-a1e0-c7ce61e011de.png)

- choose VPC only,give it name and enter IPV4 CIDR,click create VPC
![image](https://user-images.githubusercontent.com/120786669/228117561-7c72bb54-66ec-460f-9251-65b80ccc2984.png)

### Create subnets
- go to subnets tab and click create subnet
![image](https://user-images.githubusercontent.com/120786669/228117681-2c138077-94c9-4d0a-914e-e029a490a177.png)

- select the VPC that was created earlier
![image](https://user-images.githubusercontent.com/120786669/228117864-c08b5f77-0acb-40c0-b5fb-363381f8b3b5.png)

in subnet section,we will create 2 subnets i.e. public subnet and private subnet
- public subnet.give it name,choose AZ, and enter IPV4 CIDR
![image](https://user-images.githubusercontent.com/120786669/228118708-38837b04-3e31-4d08-a9d6-364574c98055.png)

- click add new subnet
- private subnet.give it name,choose AZ, and enter IPV4 CIDR. click create subnet
![image](https://user-images.githubusercontent.com/120786669/228119251-4dd2add3-6dad-4bfb-a55b-ac4c345d86d1.png)

## Launch instance 
we will create 2 instances, first instance is public instance and use public subnet.while the second private instance use a private subnet.

### public instance 
- do duplicate tab in browser,search EC2 and click EC2
![image](https://user-images.githubusercontent.com/120786669/228119518-08f8edcb-95c4-4ab3-8599-42c83b78c336.png)


- go to instances tab, and click launch instance
![image](https://user-images.githubusercontent.com/120786669/228119576-0e79a051-1c76-46da-a5f1-03d456b0e167.png)

- give it name
![image](https://user-images.githubusercontent.com/120786669/228130102-9dea4864-2daf-452f-a6bd-25ee967dae0d.png)

- click create new key pair
![image](https://user-images.githubusercontent.com/120786669/228120054-be1b5120-42a1-4d73-b541-ad46fe5116c5.png)

- give it name,choose key pair type and the format is .pem,click create key par
![image](https://user-images.githubusercontent.com/120786669/228120126-6e910495-beb4-40ca-a303-96bbc86bae98.png)

- select the key pair that we created earlier
![image](https://user-images.githubusercontent.com/120786669/228120378-e71545c0-5367-47cd-8a8d-acb43a1af9a8.png)

- on network setting click edit,and choose ur VPC and select public subnet.see that auto-assign public IP is disable because we haven't enabled yet so, we have to enabled first.
![image](https://user-images.githubusercontent.com/120786669/228120955-5bee9de2-b50b-4adc-8723-160a2c3b6242.png)

- switch to VPC and go to subnet tab, choose public subnet and click action select edit subnet setting  
![image](https://user-images.githubusercontent.com/120786669/228120932-fd8d6395-8274-45bf-9dd8-2745fcf25c66.png)

- check enable auto-assign public IPV4, click save 
![image](https://user-images.githubusercontent.com/120786669/228121277-6c442afc-8bb3-46d7-a66d-628ee1ccb60c.png) 

- switch to EC2 and refresh subnet,then auto-assign will be enabled
![image](https://user-images.githubusercontent.com/120786669/228121365-032c1bad-c32a-49b5-89b6-2a8c38ed1ffd.png)

- create new sg,create rule where instances can be SSH anywhere.click launch instance
![image](https://user-images.githubusercontent.com/120786669/228121603-ab79859e-8fa3-47fb-a1b1-91b8f09cee9f.png)

- wait until the instance is running and click connect
![image](https://user-images.githubusercontent.com/120786669/228121692-f352ee06-ce42-4365-ab85-896ce8fe0386.png)

- copy example, and paste on cmd. see that instance can't remote yet
![image](https://user-images.githubusercontent.com/120786669/228121785-400588f2-a38d-4bc2-8ca8-3cd40c635705.png)


## create igw and route table 
if you want the instance to be able to access the internet and be able to be remote, we have to first set the internet gateway and route table.

### Internet gateway
It is needed to make the public subnet in a vpc connect to the internet

- swith to VPC and go to internet gateways tab,click create internet gateway
![image](https://user-images.githubusercontent.com/120786669/228122778-81ef0496-13e6-48e0-a51a-eefa2e25517b.png)

- give it name and click create internet gateway
![image](https://user-images.githubusercontent.com/120786669/228122818-87d8719a-4c9c-4931-abfe-8381094a9a05.png)

- click action and select attach to VPC
![image](https://user-images.githubusercontent.com/120786669/228122927-76570635-6a52-4ecd-a98f-abf62ed817af.png)

- choose ur VPC, click attach internet gateway
![image](https://user-images.githubusercontent.com/120786669/228122989-48273bd7-e339-4176-92ab-0ddd14db25b3.png)

- look at the VPC ID on the igw that we created, it will change to our VPC
![image](https://user-images.githubusercontent.com/120786669/228123347-ec7118e2-bec3-44f2-9b95-50edfe286496.png)

### Route table
Route table is VPC router whose function is to route traffic between subnets and can be attached to one main route table and associated with multiple subnets

- go to route tables tab and click create route table
![image](https://user-images.githubusercontent.com/120786669/228123880-d0b0facf-6d80-477b-b69b-94a6d883e6ec.png)

#### public subnet
- give it name,and choose ur vpc.click create route table
![image](https://user-images.githubusercontent.com/120786669/228123977-06dee337-0387-4500-bfef-b89b2521c4f0.png)

#### private subnet
- click create route table,give it name,and choose ur vpc.click create route table
![image](https://user-images.githubusercontent.com/120786669/228124149-cd136a99-8c40-43dc-889e-d279bd1645f6.png)

### associate subnets to the route table
- choose public-rt, go to subnet associations and click edit subnet associations
![image](https://user-images.githubusercontent.com/120786669/228124566-fc3435b8-71c5-48b8-b096-94d4992fb834.png)

- choose public subnet and click save association
![image](https://user-images.githubusercontent.com/120786669/228124657-91bbb460-d19c-4260-910a-b2a62c01a066.png)

- choose private-rt, go to subnet associations and click edit subnet associations
![image](https://user-images.githubusercontent.com/120786669/228124720-a368eda8-f853-4d1d-9ae1-35a6cdcb017c.png)

- choose private subnet and click save association
![image](https://user-images.githubusercontent.com/120786669/228124752-39c7d1df-d7a1-4380-a8af-1982192f9784.png)

- choose public-rt, go to routes and click edit routes
![image](https://user-images.githubusercontent.com/120786669/228124813-638dd677-8059-4af8-924f-67411786d719.png)

- click add route,enter IP destination for anywhere,on target click internet gateway
![image](https://user-images.githubusercontent.com/120786669/228125056-9614224a-43f1-441d-a2ff-8ca64b6a9c53.png)

- choose igw that we made earlier and click save changes
![image](https://user-images.githubusercontent.com/120786669/228125167-477a404b-4b44-4d74-84d1-c05546b496c6.png)

###  verify 
- do SSH again to the instance
![image](https://user-images.githubusercontent.com/120786669/228125225-4a8e20d9-bb2d-4a68-9899-2a6199af5e73.png)

- try ping google.com
![image](https://user-images.githubusercontent.com/120786669/228125322-7fe01761-a8ae-4b10-aabe-0cd550ef3540.png)

### Private instance 
- click launch instance,give it name 
![image](https://user-images.githubusercontent.com/120786669/228125470-97f3fe1a-5601-45c3-a45c-3edb4c186920.png)

- create new key pair
![image](https://user-images.githubusercontent.com/120786669/228125508-2006b34a-f520-475b-b180-ca4eab2a35fc.png)

- enter name for key pair,choose key pair type and format key .pem.click create key pair
![image](https://user-images.githubusercontent.com/120786669/228125545-4ea31a32-ea67-4369-92e5-fd8169419b0b.png)

- choose key pair
![image](https://user-images.githubusercontent.com/120786669/228125702-744ae831-885a-4189-b498-a420ca0ce7ad.png)

- in network setting section, select ur vpc,private subnet, and disable for auto-assign IP public
![image](https://user-images.githubusercontent.com/120786669/228125815-df0c7b9a-37bc-48c9-9bd3-170514bb70b1.png)

- create new sg, select custom and change target for igw from public instance, click lauch instance
![image](https://user-images.githubusercontent.com/120786669/228126187-c5d696bb-311f-4c27-bbfd-bb8f0044a3ba.png)

- it can be seen that private instance only have private IP 
![image](https://user-images.githubusercontent.com/120786669/228126393-0e7daa0e-9454-48d7-8855-927c67743aee.png)

## Verify and Testing
- choose private instance and click connect
![image](https://user-images.githubusercontent.com/120786669/228126505-64b7c1d9-aae1-483e-a0c7-9d9b83978b2e.png)

- copy and and see that the instance cannot be remoted from the public instance
![image](https://user-images.githubusercontent.com/120786669/228126566-764c3d7f-f254-4f66-8bfe-e1ca956c3af8.png)

- open ur key pair from laptop,and copy then paste on this file

![image](https://user-images.githubusercontent.com/120786669/228126958-f2ae2bfa-0042-465a-bb6d-bad44ca302c6.png)
![image](https://user-images.githubusercontent.com/120786669/228126981-c10f4693-f619-455d-b94a-5532f1cc31f9.png)

- give execute permissions on privateinstance.pem and try ssh again 
![image](https://user-images.githubusercontent.com/120786669/228127051-f9fcd3dd-a96e-4a23-9e04-3bd35d831dde.png)

### WELL DONE!! FINALLY SUCCESSFUL
noted :
the reason why only public instances are allowed access to private instances is because security.
the web server is accessible to everyone and that's okay. but if the database or other configuration is clear it shouldn't be accessed by just anyone.
so we have to do this configuration, so that the database and other configurations remain safe.


## Social Proof

[Twitter ](https://twitter.com/tiaradwim1306/status/1640574185499136001)
