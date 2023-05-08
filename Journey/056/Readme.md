# meet 11 | computing,network,alert (mentor : Dea Tristianti)

## Introduction
on this journey we will learn easy stack, some of the things we will do this time are :
- create networks & subnets
- create key pair
- create instances
- connect instance to internet (router & floating ip)

verify :
- try SSH instance on local
- monitoring with alerts
- make sure that get a warning email from alerts

## Cloud Research
### create networks & subnets
- click service catalog and choose network
![image](https://user-images.githubusercontent.com/120786669/236716836-5c6b0e16-d8ee-4cf9-a882-c067c54b780e.png)

- click create network
![image](https://user-images.githubusercontent.com/120786669/236717021-8644398f-ba25-42fb-98a1-7cd0387a097d.png)

- give it name,and enter IPV4 subnet you need
![image](https://user-images.githubusercontent.com/120786669/236717049-97935c55-90fd-4453-b54f-814f5bd4feb8.png)

- click advanced configuration and add address pool range.click create network 
![image](https://user-images.githubusercontent.com/120786669/236717150-b2d765fd-4d16-42a1-b39d-b04818b1cf8b.png)

### create key pair
- choose SSH Key Pair on service catalog 
![image](https://user-images.githubusercontent.com/120786669/236717282-704d0581-2694-4526-94f2-2900d3a097e2.png)

- click create key pair
![image](https://user-images.githubusercontent.com/120786669/236717353-f1ac893c-928d-414d-962a-f9b39226fa48.png)

- give name for key pair,click create
![image](https://user-images.githubusercontent.com/120786669/236717392-6bcf2b7d-c7c8-4d74-9402-24189132c801.png)

- copy private key 
![image](https://user-images.githubusercontent.com/120786669/236717440-0cb1765e-66be-4aa0-8678-7f80ea085148.png)

### create instance 
- choose instance on service catalog 
![image](https://user-images.githubusercontent.com/120786669/236717500-e85b6729-1a27-4311-bc45-641037f822b4.png)

- click create instance 
![image](https://user-images.githubusercontent.com/120786669/236717546-99ae511b-3d94-4f0b-87c1-abb90aa3fd81.png)

- select image you needed
![image](https://user-images.githubusercontent.com/120786669/236717676-94ca5630-b9db-416b-80b7-da992dd3e5ea.png)

- then choose how much capacity you need
![image](https://user-images.githubusercontent.com/120786669/236717728-4ba2031a-0e89-4515-9d5f-5190a4668e3f.png)

- check delete with instance and click next...
![image](https://user-images.githubusercontent.com/120786669/236717742-0f9bafab-adfd-4d65-a20b-3247e83e6987.png)

- select network & subnet that we created earlier,click next
![image](https://user-images.githubusercontent.com/120786669/236717858-5561a897-3611-4c68-bc5f-51537049ef3c.png)

- give it name for instance and choose key pair we made earlier,click next
![image](https://user-images.githubusercontent.com/120786669/236717851-96ff7c3e-f027-407f-95eb-3accfd18892f.png)

-  review and click create instance 
![image](https://user-images.githubusercontent.com/120786669/236717922-03e15352-b19e-4ba0-ae57-a8a92a68daf3.png)

- wait until the instance status becomes active
![image](https://user-images.githubusercontent.com/120786669/236718055-046dce7d-11b8-4da5-b740-f52485b0b591.png)

### connect instance to internet (router & floating ip)
- choose router on service catalog 
![image](https://user-images.githubusercontent.com/120786669/236718229-50b02bda-44f2-4638-9294-3e5e74a063ea.png)

- click the router that is already available or has been made
![image](https://user-images.githubusercontent.com/120786669/236718742-8afcab0b-7f5b-46ab-ac6d-d58d16ef5a66.png)

- click connect subnet
![image](https://user-images.githubusercontent.com/120786669/236718769-d58a6f4e-10ed-4ab1-8a5c-3b15de5a52f1.png)

- in tab subnet choose subnet that was created earlier,and click connect
![image](https://user-images.githubusercontent.com/120786669/236718977-49199f76-1114-4d35-937d-b81287e0b240.png)

- click floating IP tab then click apply for IP to project 
![image](https://user-images.githubusercontent.com/120786669/236719126-cf0e5b36-98f2-4402-8611-63effef4e126.png)

- enter the size you need
![image](https://user-images.githubusercontent.com/120786669/236719138-8fe942ba-29e5-4f5b-afe2-39cca8c8e856.png)

- this is the public ip we get.
![image](https://user-images.githubusercontent.com/120786669/236719357-dde4e00a-b48e-455d-bd98-47f4bf92fb73.png)

- we must first attach the public ip to our instance. click more choose associate to vNIC 
![image](https://user-images.githubusercontent.com/120786669/236719371-15ebc405-3258-485f-b45d-72f1b7f19f00.png)

- choose our instance and vNIC will adjust
![image](https://user-images.githubusercontent.com/120786669/236719804-d5960d33-25d6-42de-8b19-9ae9a895e463.png)

## verify 
### try SSH instance on local
- open puttygen 
![image](https://user-images.githubusercontent.com/120786669/236720164-cf935bf2-43a8-49c2-8547-7997c328632c.png)

- on tab conversions click import key 
![image](https://user-images.githubusercontent.com/120786669/236720325-c1c4f637-4912-4f1c-92aa-ab6c62e669ab.png)

- select file where you save the private key
![image](https://user-images.githubusercontent.com/120786669/236720371-176d59f3-08c7-4733-99e7-c734a1ac7cf3.png)

- wait for minute and click save private key
![image](https://user-images.githubusercontent.com/120786669/236720650-69459b29-7f55-4066-a4db-95421aaaf8b0.png)

- click yes, save without passphrase
![image](https://user-images.githubusercontent.com/120786669/236720795-00429560-86bd-4deb-a374-d1a99e904025.png)

- give name for public key,and format file is .ppk
![image](https://user-images.githubusercontent.com/120786669/236720859-07d9cd8a-110e-46d2-9699-d8ab47704b7c.png)

- open putty
![image](https://user-images.githubusercontent.com/120786669/236720983-b6f8896b-58a6-4726-8cb6-e54f68de0514.png)

- choose connection,SSH,then auth,click browser 
![image](https://user-images.githubusercontent.com/120786669/236720997-f2f4bd73-0c35-493b-b559-ec0978b3f1e4.png)

- choose key you saved earlier 
![image](https://user-images.githubusercontent.com/120786669/236721151-0507fd0f-845d-4785-8dce-ba5cd96a9594.png)

- and we will ssh with this private key 
![image](https://user-images.githubusercontent.com/120786669/236721154-e6e78707-f0c6-4ae1-b654-0a71609642ec.png)

- go to session tab,enter your ip public intance and click open
![image](https://user-images.githubusercontent.com/120786669/236721280-e7868855-d64f-4be8-8a3b-7a40956e97ac.png)

- click accept
![image](https://user-images.githubusercontent.com/120786669/236721327-f2aa9ea1-2955-4846-a6e0-459c2cb55c77.png)

- result, try login with user root
![image](https://user-images.githubusercontent.com/120786669/236721350-f5908953-646d-428e-82f6-1d4c24f48f3f.png)

- try to ping google.com and make sure instance can access internet
![image](https://user-images.githubusercontent.com/120786669/236721411-854f7106-3a26-4962-b2eb-d4f3a519ec73.png)

#### and finally instance can access internet

### monitoring with alerts 
- choose alerrt management on service catalog 
![image](https://user-images.githubusercontent.com/120786669/236721758-715da700-f24a-450b-8384-8498fca8aa1b.png)

- click create alert
![image](https://user-images.githubusercontent.com/120786669/236721829-cc87e542-f312-4437-9db5-2e4c2593d207.png)

- select your instanc,click next
![image](https://user-images.githubusercontent.com/120786669/236721872-9d185030-0ebb-4199-9b97-d36cf1e4adf1.png)

- give name for alert,then enter your periodic and click automatically fill in the description.then a description will appear according to the periodic that has been selected.click next
![image](https://user-images.githubusercontent.com/120786669/236722787-14f3f92e-91e6-4e68-9593-ca80a9953aa8.png)

- click create contact info
![image](https://user-images.githubusercontent.com/120786669/236722897-a01bde38-cfaf-4020-bcd3-112d849193f6.png)

- give name for contact,enter your email.click create
![image](https://user-images.githubusercontent.com/120786669/236722980-e01e0cee-e22b-428a-8d6c-6eb87f2783af.png)

- setting your notification and choose your email for notify 
![image](https://user-images.githubusercontent.com/120786669/236723038-26367211-1fcf-4c54-82b1-4239be028405.png)

- result
![image](https://user-images.githubusercontent.com/120786669/236723174-950801f3-bf51-41b2-adc1-df23e790d0b1.png)

- wait untill get email alarm like this 
![image](https://user-images.githubusercontent.com/120786669/236723227-f1fbdd17-ec8a-485d-8998-ffcff9f9d070.png)


## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1655407314168606720)
