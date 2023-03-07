# Meet 6 | EBS & AMI hands on (mentor : yosep kusuma wibawa)

## Introduction
EBS hands on :
- create instance & volume
- attach the volume to the instance
> - attach volume in the same AZ
> - attach volume in different AZ
- delete on termination
- snapshot volume

AMI hands on :
- launch instance with just install apache
- create ami
- launch instance based on AMI with index.html

## Cloud Research
## EBS ( Elastic Block Store )

### create instance & volume 
- create instance,we have an instance that has one volume of 8 GB and in AZ us-east-1a
![image](https://user-images.githubusercontent.com/120786669/223318670-e09863e7-e72c-4d9b-b482-23c836ec4e42.png)

- go to the volume tab, and click create volume
![image](https://user-images.githubusercontent.com/120786669/223318776-e36b671f-886f-481a-9067-b077b0e387d4.png)

- create a volume with the same AZ as the instance's AZ, us-east-1a
![image](https://user-images.githubusercontent.com/120786669/223318967-f65ddfff-af18-4e49-bd6d-8c43a6cc3e68.png)

- scroll and click create volume
![image](https://user-images.githubusercontent.com/120786669/223319011-afa0481b-3241-4e80-8bc5-d918c2a46b0d.png)

- then there will be 2 volumes, one primary volume belonging to the instance and the second volume we just created.
![image](https://user-images.githubusercontent.com/120786669/223319338-49cd9d4a-8763-4969-9229-2a922940849c.png)

### attach the volume to the instance
#### attach volume in the same AZ
- select the volume we just created, click action and select attach volume
![image](https://user-images.githubusercontent.com/120786669/223319635-44874eda-e98e-49e1-9fb1-d1b205652cc8.png)

- choose volume we have created and click attach volume
![image](https://user-images.githubusercontent.com/120786669/223319834-9db55556-a71c-4510-9137-ca1c1cc2c5d4.png)

- verify that now,there are 2 existing volumes in our instance
![image](https://user-images.githubusercontent.com/120786669/223320103-61e1dc88-1beb-4029-af7b-a5eae27a7a2d.png)

#### attach volume in different AZ
- click create volume and create a volume in a different AZ than the instance's AZ,
example : us-east-1b
![image](https://user-images.githubusercontent.com/120786669/223320463-8b6a224e-10a4-4580-bf94-9b7ce739d452.png)

- choose volume we have created and click attach volume
![image](https://user-images.githubusercontent.com/120786669/223320876-4cfde7b7-aac6-49bb-92da-43943c9a0aa0.png)

- then no instance selection will come out because none of the instances are in the same AZ
![image](https://user-images.githubusercontent.com/120786669/223320996-c463c5e1-a058-48b8-b21f-7ed993fdf1fb.png)

### delete on termination 
when created an instance there will be an option to delete storage when the instance is terminated or not, and by default storage will be deleted when the instance is terminated

- the first volume is the primary volume which will be deleted when the instance is terminated while the second volume that we create will not be deleted when the instance is terminated
![image](https://user-images.githubusercontent.com/120786669/223322148-9a300240-8858-4188-910d-d4d5d6f2834c.png)

- go to the instance tab, choose the instance, click instance state and select terminate instance
![image](https://user-images.githubusercontent.com/120786669/223322735-8cc19c81-f228-41fb-b61e-c71e61f98786.png)

- There will be a warning that by default the volume will be deleted when the instance is terminated, click terminate
![image](https://user-images.githubusercontent.com/120786669/223322764-ef937354-8e5f-416a-8472-2e0b10a7e221.png)

- so now it only has 2 volumes, and the instance's primary volume is also deleted
![image](https://user-images.githubusercontent.com/120786669/223322966-b44d675b-c050-4b72-948c-b3d5ca48a7be.png)

### snapshot volume 
- choose volume,click actions and select create snapshot 
![image](https://user-images.githubusercontent.com/120786669/223323437-148cd889-d66b-4618-9ae6-8e7f1c6882ff.png)

- leave by default and click create snapshot
![image](https://user-images.githubusercontent.com/120786669/223323462-0639a4a9-6c29-48b7-8012-c3a3cf22a0f9.png)

- go to snapshot tab,choose snapshot click action and select create volume from snapshot
![image](https://user-images.githubusercontent.com/120786669/223323785-256a2275-d8dc-4eb1-9e86-c6b6d55ab99a.png)

- with snapshot we can create volume with different AZ
![image](https://user-images.githubusercontent.com/120786669/223323859-b5cf2c15-96c1-41af-9491-69ca0d9d4b00.png)

- go to volume tab,check that there will be 2 volumes, the first is the volume that we snapshot and the second is the volume of the snapshot.and they have different AZ 
![image](https://user-images.githubusercontent.com/120786669/223324060-f29f45e1-4247-4432-b462-971172a3abb2.png)

## AMI (Amazon Machine Image)
### launch instance with just install apache
- launch instance and give it a name
![image](https://user-images.githubusercontent.com/120786669/223324820-a743db97-fb3f-4072-bed6-736f46d62716.png)

- configure as usual,script for user data 
![image](https://user-images.githubusercontent.com/120786669/223324921-e0c1197b-562c-4b1e-b032-2b6140fcff13.png)

- click launch instance 
![image](https://user-images.githubusercontent.com/120786669/223325260-b5b684aa-0eb3-47ed-a6c7-ea1914b837ec.png)

- access ip public on web browser 
![image](https://user-images.githubusercontent.com/120786669/223325327-048af744-64bb-49d4-a3c7-6a791bc871d1.png)

### create ami
- choose instance,click actions select image and templates and choose create image
![image](https://user-images.githubusercontent.com/120786669/223325518-a48c6a93-5645-4804-97ea-a7f28f39af10.png)

- give it a name 
![image](https://user-images.githubusercontent.com/120786669/223325577-c01d73ec-271d-4e22-ab4d-4c71787464b2.png)

- leave by default and click create image
![image](https://user-images.githubusercontent.com/120786669/223325595-e9f24d78-e4e0-494a-bc64-7a427671f107.png)

### launch instance based on AMI
- go to AMIs tab,choose ami and click launch instance from AMI 
![image](https://user-images.githubusercontent.com/120786669/223325679-8dab6da1-ddc3-4d39-9fad-d69aa2cd996f.png)

- give it a name
![image](https://user-images.githubusercontent.com/120786669/223325786-839765b6-0034-4c50-baab-eafd891b862c.png)

- you can see we use our own AMI
![image](https://user-images.githubusercontent.com/120786669/223325831-52cf2b12-c4c6-4374-a4ee-558d534bb4f5.png)

- we can also change some settings such as where our AZ is located
![image](https://user-images.githubusercontent.com/120786669/223325943-2f3a0273-4de3-42ea-8564-b386a7baf88d.png)

- add this script for edit index.html
![image](https://user-images.githubusercontent.com/120786669/223326088-43ed0cf7-8ed9-441c-933a-4edace73fe7b.png)

- click launch instance 
![image](https://user-images.githubusercontent.com/120786669/223326229-fa7f9410-85f4-4835-b552-bd2261171f83.png)

- now, access the public ip of the new instance in the web browser
![image](https://user-images.githubusercontent.com/120786669/223326418-1c0b63d0-67a2-48b8-b805-e927da953ca7.png)


## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1632977227947343876)
