# Storage - Easy stack 

## Introduction
on this journey we will learn easy stack, some of the things we will do this time are :
### Volume
- create volume
- attach a volume to instance
- detach a volume from instance 
- edit volume 
- extend volume
- create image using volume 
- modify volume property 
- delete volume
### Volume Snapshot 
- create volume snapshot
- edit volume snapshot
- create a volume using volume snapshot
- delete volume snapshot
### Volume Backup
- create volume backup
- restore volume using the backup 
- delete volume backup

# Cloud Research
## Volume 
### create volume 
- choose volume on service catalog 
![image](https://user-images.githubusercontent.com/120786669/236982691-03c70b78-5af8-4f95-8cba-5093944a22cb.png)

- click create volume
![image](https://user-images.githubusercontent.com/120786669/236982820-f48c3bf9-d283-4268-bb1c-c71807de94df.png)

- give name for volume and specify the volume size you want,click create 
![image](https://user-images.githubusercontent.com/120786669/236982864-7986dc03-41bf-41e0-a07e-d500991d2094.png)

- wait untill status state becomes Available
![image](https://user-images.githubusercontent.com/120786669/236983114-8e741192-7c55-4b36-943e-a15283d57cbf.png)

### attach a volume to instance
A volume can be attached to an instance as a block device where the instance can store data. A volume can be concurrently attached to only one instance.
- choose volume and then click attach
![image](https://user-images.githubusercontent.com/120786669/236984027-b23c3363-b081-4865-9012-b203f59a28ab.png)
- select the instance you want to increase the volume for.click attach
![image](https://user-images.githubusercontent.com/120786669/236984158-c8911a61-762b-439d-a621-890917a7d4a7.png)
- then the status is already in use, which means that this volume is already in use
![image](https://user-images.githubusercontent.com/120786669/236984483-f72e9d27-e24b-4957-9323-2247aecb4c7a.png)

### detach a volume from instance 
- To unmount a volume from an instance, select the volume and click Detach.
![image](https://user-images.githubusercontent.com/120786669/236984822-bf2981ce-f029-4037-bbcb-1647faa95ecd.png)
- click detach
![image](https://user-images.githubusercontent.com/120786669/236984848-d7f05789-f5f9-4226-9bb2-858b4bc3ff96.png)
- and the status returns to available
![image](https://user-images.githubusercontent.com/120786669/236984893-f5889abd-9e9e-4ed3-bf72-8b2e65184b1c.png)

### edit volume 
- If you need to modify basic volume information, such as the name and description,select the volume then click more and choose edit
![image](https://user-images.githubusercontent.com/120786669/236985108-ae65907e-f719-4db2-a850-86aa3d4b31d6.png)
- try to change name and add description,then click save
![image](https://user-images.githubusercontent.com/120786669/236985129-7ef981ff-d425-4189-aaab-278b3b1f7736.png)
- and name has changed
![image](https://user-images.githubusercontent.com/120786669/236985192-7fcbfec8-d81e-47a2-974a-3222b5f678ee.png)

### extend volume
If the size of a volume in the Available and In use state cannot meet service requirements, you can expand the volume size for larger capacity.
- select the volume and click more then choose extend size
![image](https://user-images.githubusercontent.com/120786669/236985291-002b22c9-2db8-4fda-96e0-d7169cf156e9.png)
- Specify the volume size and click Extend.
![image](https://user-images.githubusercontent.com/120786669/236993660-7d45ec99-9a35-48c3-bb8c-6b1027227ac6.png)
- The system displays the notice “After expansion,the volume can no longer be reduced.”. Click Confirm.
![image](https://user-images.githubusercontent.com/120786669/236993756-23205b6a-3b73-4a9e-8ab2-24e3e08bcc12.png)
- You can see that the size has changed
![image](https://user-images.githubusercontent.com/120786669/236994883-aaea9475-ef24-4554-8d17-1420ce9f46f9.png)

#### note : 
- After expanding the volume capacity, you must log in to the instance and manually modify the file system configuration to make the additional capacity take effect.
- If an expanded volume has not been attached, the capacity expansion takes effect immediately after you attach the disk to a instance
- Because the volume capacity that has been changed cannot be reduced, you are advised to set a proper capacity during expansion
- After expanding an In-use volume, if the boot source kernel version of the instance mounted on the volume is too low, you may not see the additional capacity in instance. In this case, detach the disk and reattach it, or stop theinstance and then start it.

### create image using volume 
A volume can be used to create an instance image. It is recommended that you create an image in RAW format. This function is usually used by common users to create a required ISO format image in the project.
- select the volume and click more then choose create image
![image](https://user-images.githubusercontent.com/120786669/236995077-f8a379ab-a29c-4d70-919d-fd479af0f624.png)
- enter a name for the image then add the minimum RAM and click create
![image](https://user-images.githubusercontent.com/120786669/236995309-b0dcc76f-8c05-45ad-9106-c0093f24588e.png)
- verivy,choose instance image on service catalog 
![image](https://user-images.githubusercontent.com/120786669/236995835-ab2ce4e8-1e61-4392-bd0b-2279ee440e6c.png)
- and we successed create instance image from volue
![image](https://user-images.githubusercontent.com/120786669/236995924-42da4b94-6c70-4667-8a8e-c379bdbbb980.png)

### modify volume property 
- You can perform the operation of modifying the volume property on the volumes that are in the available state under the project.
You can perform the operation of modifying the volume property on the volumes that are in the available state under the project.
- If the current property of the volume in the in use state is non-bootable, you can modify the volume property to bootable, and then users under the same project can use the bootable volume to create a new instance.
- For volumes in the in use state, you cannot perform modifying property operations. In addition, depending on the volume attach point, the property of the volumes in use will be displayed as root disk and data disk respectively.
![image](https://user-images.githubusercontent.com/120786669/236996026-9fc1e06e-847e-4e03-95e3-9ef16002f19c.png)
- select the volume and click more then choose modify property 
![image](https://user-images.githubusercontent.com/120786669/236996778-c28f9565-7f28-4f68-96f5-247db4a35b2c.png)
- click confirm
![image](https://user-images.githubusercontent.com/120786669/236996879-4dd4a0c5-53db-4065-b16e-a9ea37fb396d.png)
- and property already change
![image](https://user-images.githubusercontent.com/120786669/236996924-32409fbe-2838-4e48-9faa-dba58af1bb22.png)

## Volume Snapshot 
### create volume snapshot 
- select the volume and click create snapshot 
![image](https://user-images.githubusercontent.com/120786669/236997113-9966ffe7-b4e1-4b85-91af-975be6c349c3.png)
- give name and click create
![image](https://user-images.githubusercontent.com/120786669/236997252-3b640583-0fdf-412f-9928-94fcd54b522b.png)
- wait untill state become Available 
![image](https://user-images.githubusercontent.com/120786669/236997295-5d51361b-01bd-4e65-814f-997b82883177.png)
- When we create a snapshot of a volume, we can check what snapshots were made of that volume by going to details about the volume on the snapshot tab.
![image](https://user-images.githubusercontent.com/120786669/236997394-8a753dc8-bd52-464f-808d-4964839c0b3a.png)

### edit volume snapshot
- select snapshot then click more and click edit
![image](https://user-images.githubusercontent.com/120786669/236997562-7a579848-8ca6-406e-8acf-2216a95112c2.png)
- try to change name,click save
![image](https://user-images.githubusercontent.com/120786669/236997620-df566f7a-aa43-4a69-b1be-ff78df1f64e1.png)
- the name of the snapshot has changed
![image](https://user-images.githubusercontent.com/120786669/236997669-85bd36f4-6f6e-48ee-a9ca-7a541062e88b.png)

### create a volume using volume snapshot
#### first step
- select snapshot and click create volume
![image](https://user-images.githubusercontent.com/120786669/236997827-fa683daa-31ab-437e-9443-468c5159cecc.png)
- we can change name and size or add description,click create
![image](https://user-images.githubusercontent.com/120786669/236997843-62f69b32-6a66-45a6-9b65-5c7032d55101.png)
- result 
![image](https://user-images.githubusercontent.com/120786669/236997963-db638540-10d6-47eb-81e1-36473e0c1e00.png)
#### second step 
- check what snapshots were made of that volume by going to details about the volume on the snapshot tab.and click create volume in the snapshot you want
![image](https://user-images.githubusercontent.com/120786669/236998193-b59dba01-4240-4388-9009-4676a1247a2c.png)
- we can change name and size or add description,click create
![image](https://user-images.githubusercontent.com/120786669/236998452-b5789a46-80a7-4fbe-a6ee-6262471863c6.png)
- result,volume source from volume snapshot that was created earlier
![image](https://user-images.githubusercontent.com/120786669/236998495-ab973a87-e4b7-4d76-9fd0-12f4feed7444.png)

### delete volume snapshot
- select the volume and click delete
![image](https://user-images.githubusercontent.com/120786669/236998817-baa59321-292f-4fd4-868c-874698c882cf.png)
- click delete
![image](https://user-images.githubusercontent.com/120786669/236998862-c3c0b0d9-d3de-4ef2-81ef-3ff75fa34479.png)
- click confirm 
![image](https://user-images.githubusercontent.com/120786669/236998903-9cc42b4d-787c-452e-a734-8525a61f04e3.png)

## Volume Backup 
### create volume backup
- select the volume then click more and choose create backup
![image](https://user-images.githubusercontent.com/120786669/236999082-a14c092f-49e9-412c-b2c8-e0d696bf5d35.png)
- enter name for backup and choose full backup for type,clcik create
![image](https://user-images.githubusercontent.com/120786669/236999189-73c110cb-af55-432e-951e-02f3c3ebe569.png)
- select the volume then click more and choose create backup
![image](https://user-images.githubusercontent.com/120786669/236999435-b60ad3e2-0791-4d4e-b094-112d523f49b5.png)
- second, choose incremental for type 
![image](https://user-images.githubusercontent.com/120786669/236999495-dcad7a58-9632-4ac7-8f9e-d30e3de39a63.png)
- go to volume backup tab and u can see 2 volume backup that was made earlier
![image](https://user-images.githubusercontent.com/120786669/236999511-8c6118c6-bd92-44e9-8001-ba0200cffad3.png)

### restore volume backup
- select the volume backup then click restore volume backup
![image](https://user-images.githubusercontent.com/120786669/236999677-db1c8e7b-a5bc-4e8d-bddb-b4b715aa815c.png)
- choose create a new volume and give name,click restore
![image](https://user-images.githubusercontent.com/120786669/237000261-c65b1661-746b-4ce9-8bb7-d4c0a96507e0.png)
- so,state become restoring 
![image](https://user-images.githubusercontent.com/120786669/237000378-e106df0f-5d0f-4695-b8fd-387ec9f07b01.png)
- go to volume tab and see the result 
![image](https://user-images.githubusercontent.com/120786669/237000445-beeba806-2d8c-4862-aafd-30a905788cb8.png)

### delete volume backup
- choose the volume backup  and click delete 
![image](https://user-images.githubusercontent.com/120786669/237000563-3f4b0ef6-72fb-4264-b74d-5a3cbde3acb4.png)
- click delete
![image](https://user-images.githubusercontent.com/120786669/237000640-0c37b531-1ba2-4ae6-8079-7eb6fe91c850.png)
- click confirm
![image](https://user-images.githubusercontent.com/120786669/237000660-7018b726-f5d0-43d5-895d-d3904779aef1.png)
Do the same for the second backup volume

### Delete Volume
- click volume that you want to delete,click more and choose delete
![image](https://user-images.githubusercontent.com/120786669/237000800-cf9d6a98-56b9-45a3-a73f-cb37c3d42bc6.png)
- click delete
![image](https://user-images.githubusercontent.com/120786669/237000933-7289dc50-260a-40a0-b18e-b117a3cbb281.png)
- click confirm  
![image](https://user-images.githubusercontent.com/120786669/237000955-131d0a01-c91d-4873-be41-5835d615fee5.png)


## Social Proof
[Twitter](https://twitter.com/tiaradwim1306/status/1655806466182504449)
