# meet 8 | static website with S3 (mentor : yosep kusuma wibawa)

## Introduction
after graduating from SMK we will definitely work. For this reason, personal branding is needed, one of which is a portfolio.
at this meet we will create a portfolio with static web hosting with S3,
scenario : [link drive](https://drive.google.com/drive/folders/1bvDF29fPWj0Oa__9FShqNdNa17Hjv5CQ?usp=sharing)

## Cloud Research
### create bucket
- search S3 and click S3
![image](https://user-images.githubusercontent.com/120786669/227778652-4e14cb17-517e-459a-9db0-fc93a430b1ec.png)

- click create bucket
![image](https://user-images.githubusercontent.com/120786669/227778673-f4a9f211-0e02-46d0-85ee-2ceffea1ad6d.png)

- give it name, name for bucket must be unique
![image](https://user-images.githubusercontent.com/120786669/227778697-b11153ec-ca27-4ca5-9a07-a995f63a129b.png)

- uncheck block all public access, so that the bucket is publicly accessible
![image](https://user-images.githubusercontent.com/120786669/227778720-d52ba1d8-2955-4f1b-84d3-e8787f0e9e46.png)

- enable bucket versioning
![image](https://user-images.githubusercontent.com/120786669/227778830-109e03b1-38b5-4768-aa6a-2000aeed907e.png)

- click create bucket
![image](https://user-images.githubusercontent.com/120786669/227778837-b85fccc0-e138-453f-80d0-9975aa54e4d4.png)

- click the bucket that we created earlier
![image](https://user-images.githubusercontent.com/120786669/227778890-41e6a0e8-7b42-4175-accd-9bfce8654651.png)

### bucket policy
- in tab permissions scroll and find bucket policy, click edit
![image](https://user-images.githubusercontent.com/120786669/227778960-454e4e1a-8084-409d-ae71-f075c3f0d1c2.png)

- click policy generator,we will create policy with JSON format with this
![image](https://user-images.githubusercontent.com/120786669/227778988-b002a9f4-0a52-48fc-bf62-cda8086c4c20.png)

- Select type, insert principal to * Select action to getObject
![image](https://user-images.githubusercontent.com/120786669/227779229-b91aae69-4b4e-409c-9168-f5073d888427.png)

- back to bucket policy tab and copy your ARN
![image](https://user-images.githubusercontent.com/120786669/227779260-b82822c1-826c-46b6-815a-b10a47dc2c5d.png)

- paste and add /* at the end,click add statement
![image](https://user-images.githubusercontent.com/120786669/227779276-b9a4b82e-a22d-4a1c-92f0-bc491821f734.png)

- review and click generate policy
![image](https://user-images.githubusercontent.com/120786669/227779394-2135476e-254b-4ae0-8b37-86ec768f95bf.png)

- copy policy
![image](https://user-images.githubusercontent.com/120786669/227779400-e22a95e6-8567-42c9-a454-1d97028b933a.png)

- paste and click save changes
![image](https://user-images.githubusercontent.com/120786669/227779419-54380808-dc80-488e-bc6f-eaa1fe68e765.png)

- go to tab object and click aploud and add the file you want to upload
![image](https://user-images.githubusercontent.com/120786669/227779443-71b4eafc-fe44-4292-9f96-5332d9066aa4.png)

- and this is the file used in this lab
![image](https://user-images.githubusercontent.com/120786669/227779530-7f78504c-f0f9-4244-8dab-8d52b36cec10.png)

### setup static website hosting
- go to tab properties scroll and find static web hosting,click edit
![image](https://user-images.githubusercontent.com/120786669/227779610-24f39408-bd96-4490-b8e4-cecc40187607.png)

- click enable and enter your document index.html and error.html,click save changes
![image](https://user-images.githubusercontent.com/120786669/227779633-91a989a3-81a6-4a74-91ad-3e3fe7465517.png)

### Verify
### akses web 
- copy link
![image](https://user-images.githubusercontent.com/120786669/227779731-7409e8da-3fbf-4069-988d-30f3856b47c7.png)

- paste to the web browser, and this is the result
![image](https://user-images.githubusercontent.com/120786669/227779752-92ffd0ae-3d00-4c13-b9e1-8b7b6d04b30c.png)

- click curriculum vitae,and u find your cv
![image](https://user-images.githubusercontent.com/120786669/227779818-699a7309-01cf-419a-abbc-35138777684f.png)

### test page - error.html
- delete your index.html 
![image](https://user-images.githubusercontent.com/120786669/227779915-6f0216d4-7e0a-4b58-a62c-19012b448af6.png)
![image](https://user-images.githubusercontent.com/120786669/227779918-f1cc1028-2906-4834-87d0-4255bc9ccb23.png)

- refresh your web server
![image](https://user-images.githubusercontent.com/120786669/227779953-0867cd76-aa2d-40c3-9768-d2db893acbf3.png)

### returns index.html
- click show versions,and choose index.html with delete marker and click delete
![image](https://user-images.githubusercontent.com/120786669/227780000-8b52d205-f35f-46d8-a7a8-384d07d30670.png)

- insert permanently delete,click delete object
![image](https://user-images.githubusercontent.com/120786669/227780275-65843986-d33a-495f-a376-dca561eb88ba.png)

- refresh again
![image](https://user-images.githubusercontent.com/120786669/227780090-5e9fbbc0-27b4-46df-bee3-78027eda182e.png)

### Remove Resource
- choose bucket and click empty
![image](https://user-images.githubusercontent.com/120786669/227780887-846aedd0-09a3-456e-9e2e-e0d5815934b0.png)

- insert permanently delete
![image](https://user-images.githubusercontent.com/120786669/227780183-557872da-f25f-47f5-998a-b3894017a1c1.png)

- click bucket and click delete
![image](https://user-images.githubusercontent.com/120786669/227780197-c4c1ea29-7df3-417a-ac0f-2ebb4fe07a8f.png)

- enter bucket's name and click delete bucket
![image](https://user-images.githubusercontent.com/120786669/227780304-9d18897f-e165-433e-b21e-6b9fc12c11d1.png)


## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1639992079748317184)
