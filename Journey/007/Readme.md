
# Meet 2 | User & Group management, File Permissions (mentor : diana zuniarti)

## Introduction
On this journey, we will learn several things, such as:
1. Group and user management
- type - type user
- information user
- create user
- create groups and add users to groups
2. file permissions
- chmod
- chown
- chgrp

## Cloud Research
## Group and user management
### Type - type user :
![image](https://user-images.githubusercontent.com/120786669/211989651-97ac45e1-064d-42a3-a19d-8c6cb33b3e3d.png)
1. Regular user,
This user only has certain rights/privileges. This user can only use the operating system from the user's side.
ex: can only change the permissions of the user's own files, etc.

2. Administrator user,
The administrator user is root user, this user has full rights/privileges to the operating system that you are running. Starting from creating a new user, installing programs, freely changing the permissions of a file, etc.

### Information user 
you can see information of user in /etc/passwd
![image](https://user-images.githubusercontent.com/120786669/211994411-c6b18924-6267-4506-8bf3-5ed608c2a218.png)


Meaning of each number:
  1. Users
  2. Passwords
  3. UID
  4. GID
  5. User information, ex: full name, room number, etc
  6. Home directory
  7. Shell to run/execute a command

### create user
There are 2 commands that we can use to create a user :

1.useradd,
This command is used to create a normal user, creating a user with the useradd command has several drawbacks such as:
 - don't have a password, if you want a password, you have to set it manually
- do not have a home directory
- don't have grub

practice :
![image](https://user-images.githubusercontent.com/120786669/211996049-d7a1ff73-cd1c-4af8-a4c7-730fa4effd3a.png)
After create TKJ user, we try to log in to that user and it works,because we log in via root.If we log in via a normal user, the TKJ user cann't log in because we don't have a password and we have to set it manually.

![image](https://user-images.githubusercontent.com/120786669/211996133-4d2e0dc5-087a-45a1-91ed-e7dd752b32e7.png)
After we create a password, we can log in to the TKJ user, but this user cannot execute commands because he doesn't have shell access in the /sbin/bash file.
From the problems that we got earlier we have an easy solution
![image](https://user-images.githubusercontent.com/120786669/211996993-8d250354-9dcb-4d5c-a7bc-46ac4c8000d4.png)
With this command, we will create a normal user directly with shell rights and the home directory. Then we add a password so the user will be able to login with a normal user.

2.adduser,
This command is used to create an administrative user and is more secure
practice :
![image](https://user-images.githubusercontent.com/120786669/211997581-746f8d85-a249-4f04-86ad-30a759c06083.png)
Create a user with adduser is considered easier, as above :
1. Created a user
2. Create a group
3. The user is added to the group
4. Automatically created home directory
5. Asked for password directly
6. Asked for some information about the user such as full name, room number, work phone, etc

## create groups and add users to group
- groupadd
This command is used to create group.
![image](https://user-images.githubusercontent.com/120786669/212002050-cc4f2441-34a5-4d5f-b2dc-2edc6098aad7.png)
- add user to group 
There are 2 commands that we can use :
1. adduser 
![image](https://user-images.githubusercontent.com/120786669/212002276-06c02068-909d-4b3e-ba78-b1eb3df65a06.png)

Here we add user TKJ to group BATCH13, check with command -> id (user)

2. usermod -G 
![image](https://user-images.githubusercontent.com/120786669/212013061-c160ba0d-b3ae-4a49-9cf1-56cbb3420209.png)

Here we add the BDPM user in the BATCH13 group, besides the id we can also check with the command -> groups (user)

## File Permissions
This section we create 2 file for practice 
![image](https://user-images.githubusercontent.com/120786669/212004927-2fd09cb4-026d-4da9-a145-1a2c3f45792f.png)
let's see the meaning of each color :
![image](https://user-images.githubusercontent.com/120786669/212004950-158a6e4b-765a-49bf-8dba-ea2cffe0cc5d.png)

There are 3 commands that we can use for file permissions :
1. chmod
This command functions to change the permissions on a file or directory, there are 2 options that we use :
- numeric (number)
![image](https://user-images.githubusercontent.com/120786669/212006496-55fe2359-a022-4410-8e88-6f123cb7d580.png)
practice :
We will change the permissions on file1.txt which were previously rw-r—r—to rwxrw-r--
![image](https://user-images.githubusercontent.com/120786669/212006573-6bdb4802-6c8e-4f7d-a4ef-398aaf318273.png)

- alphabetic 

we will change the permissions on file1.txt, we will reduce the execute permissions on the user and add write permissions on the other
![image](https://user-images.githubusercontent.com/120786669/212007724-22e9be0a-f2b7-40e0-a160-d0db502e04aa.png)

2. chown

This command is used to change the user and group of a file or directory
practice :
We change the user and group from file2.txt which previously belonged to user root and group root to user TKJ and group BATCH13
![image](https://user-images.githubusercontent.com/120786669/212008171-36c53ae3-3670-4dbb-9b17-8a6029ee485e.png)

3. chgrp

This command is used to change the group ownership of a file or directory
change the group in file2.txt to belong to the root group as before.
![image](https://user-images.githubusercontent.com/120786669/212008257-74dbec19-542d-4f4c-a6db-5d98fb3f937b.png)
 
## Social Proof
[Twitter](https://mobile.twitter.com/tiaradwim1306/status/1613453948882681858)
