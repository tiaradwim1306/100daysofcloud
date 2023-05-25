# meet 12 | load balancer (mentor : Dea Tristianti)

## Introduction
on this journey we will learn create load balancing on easy stack, some of the things we will do this time are :
- Create instance 
- Create security group
- Add security group to instance 
- Create simple web in instance 
- Creating a Load Balancer
- Creating an HTTP Listener
- Creating a Resource Pool
- Add resource
- associate floating IP
- verify 

## Cloud Research
### Create instance 
to make load balancing we need 2 instances, and we have created 2 instances as shown below,how to create an instance can be seen in the previous journey
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/06ce91a5-df01-4152-9480-71a87f0a8530)

### Create security group
to make instance accessible by web,we need to give HTTP permissions to the instance, for that we need to create a security group
- give name for security group and click create
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/219395b2-5b8f-47dd-a1ff-070a512637f1)

- click add rule
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/cfa87c76-b70e-4176-bbcd-892a99f69a00)

- choose HTTP,for others leave it default and click add rule
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/22ce5ac2-267c-46fc-bbd3-b48aac070b52)

### Add security group to instance
- select instance,click more and choose edit security group
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/d0287247-435c-4643-bd85-7a3e5b59c280)

- then,click security group that you want to add,click save
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/c6386f54-6994-4d29-8945-dc2ade14cb4e)

### Create simple web in instance
first you must remote the instance,you can remote by keypair or password,here i use password 
#### fisrt instance 
- install httpd
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/be80e81e-4d41-47a9-bd4d-64abd7b40f0b)
- edit file index.html
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/d9d10f6b-2405-4656-b1a9-9a90a33a0796)
- enter teks that you need to display when accessed by a web server
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/718f1627-b9b0-46f0-b89f-af7de3375b35)
- start and enabled httpd service 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/e53c3682-7578-4488-bb2d-6d6090611a41)

#### second instance
- install httpd like before,then edit file index.html
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/0f08561b-4d2e-4980-b083-1785ddb23138)
- enter teks that you need to display when accessed by a web server
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/add8fde0-9d32-4009-bcd7-01f83899e7f5)
- start and enabled httpd service 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/eb10f104-f44c-4bd5-ad3f-b89fd37b668e)

### Creating a Load Balancer
- choose load balancer on service catalog
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/627be104-5f7d-4d26-b2df-966be1abe049)
- click create load balancer
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/2fc65dd0-4d05-4363-8309-883abe778651)
- give name for load balancer,and choose subnet from instance that will be used as a load balancer,here we choose auto assign to make it easier and click create
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/6d2eb391-3c2d-432a-9564-b691d4764b5f)

### Creating an HTTP Listener
To forward incoming traffic, users need to create a listener that identifies traffic transmitted in compliance with a specified protocol.
- in tab listener,click create listener
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/5150f7f5-5005-489f-ba46-1d63a240129a)
- give name,choose load balancer,choose protocol,enter port,and enter connection limit.click create
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/21659e2c-7307-499d-b24d-d617ed791eb9)

### Creating a Resource Pool
After a load balancer and a listener are created, you need to add the instance in the network to a load balancing resource pool.
- in tab Pools click create Pool
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/eb2d551d-9fc6-40b5-9765-28c21b945c7d)
- give name,choose load balancer,choose protocol and choose method,here i choose round robin because this mode is very easy to verify.click create 
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/c05925f3-4abb-424c-b012-e36b705f7c46)

### Add resource
After a load balancing resource pool is created, you can open the detail page by clicking the name of the resource pool and add instances to the pool.
- click add resource
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/526d88e0-c47e-43b6-8f57-63aa2f3e25a8)
- choose subnet,choose instance and vNIC,enter port number,and weight.
Add 2 instances we created earlier for the load balancer,that is loadbalancer-1 and loadbalancer-2
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/9c1728a8-0fa2-40f7-9321-24db859646c1)
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/8786ef35-1a2a-4e6b-958a-ca89eb7a4718)

note : When adding an instance, you need to specify Weight. The weight of an instance defines whether a load balancer takes priority in distributing network load to the instance,and at this time we give the same priority which is 1 weight

### associate floating IP
-  in tab load balacers choose the loadbalancer and click more then choose associate floating IP
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/4a15fed8-3077-40fb-94eb-287f28b35dae)

- choose your floating IP,floating IP use for access web server from loadbalancer
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/68d13d36-7ac4-433c-bc7c-f61d38544ca9)

- verify
When creating a load balancing resource pool, you can set LB Mode to one of the following types:
### mode round robin 
    Polling: The load balancer distributes traffic to instances in a resource pool in turn based on their weights. This load balancing mode is usually selected for processing short connection services, such as the HTTP service.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/6f502878-190f-457a-aafe-c37a5c425b0f)
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/fad7ceb1-701f-4f2f-86de-ad549125d4a8)
refresh page and then page will change to another web server instance
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/8d373f4e-5c25-41e6-b4b1-92f2a7a84085)

### mode least connection
for change the method,you go to pools and click pool load balancer then click more actions and choose edit.Then you can change the method
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/d7c86e8c-e77b-4917-b8f2-bc04bc639a15)

    Minimum number of connections: The load balancer preferentially sends service requests to instances with the fewest connections. This load balancing mode is usually selected for processing long connection services, such as the database connection service. If the priority of an instance in the resource pool has been adjusted, the system will distribute traffic based on the priority and current connection quantity of instances.
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/cce56f04-c7a2-4a45-b295-ffe77bc3739d)
![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/11af6f57-c395-4f83-9c4f-b6d181c0002e)

 ### mode source IP
 ![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/80d2be1d-96e1-4f73-b3d5-19a2728ebca4)

    Source IP address: The load balancer performs hash calculation using the source IP address of a request, and determines which instance to send the request to by factoring in the calculation result and instance weights. This load balancing mode enables the load balancer to send all requests of one client to the same server and applies to TCP services without the cookie function.

![image](https://github.com/tiaradwim1306/100daysofcloud/assets/120786669/5f4f4a7f-974e-446c-a0d6-5ddbe2bd79e0)

when you refresh the page many times the web server will remain the same and doesn't change
## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1661264986218565632)
