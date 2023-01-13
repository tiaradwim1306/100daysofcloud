

# EBS & AMI : Course on Udemmy by Stepahane Mareek

## Cloud Research
## EBS (Elastic Block Store)
EBS volumes are network drives that you can attach to instances as they run
- EBS allows instances to persist data, even after being terminated
- can only be attached to one instance at a time (CCP level)
- bound to a specific availability zone
- on the free tier the free EBS storage is 30 GB for General Purpose (SSD) or Magnetic per month

nb: can be analogous to 'network usb stick' 

### EBS Volume
- It's a network drive (i.e. not a physical drive)
uses the network to communicate instances and can be moved from one instance to another quickly
- It's locked to an Availability Zone (AZ)
EBS volume using a specific AZ if attached to us-east-1a cannot be attached to us-east-1b and if you want to move it must be snapshot first
- Have provisioned capacity (size in GBs, and IOPS)
drive capacity may be increased over time and there is a bill for all provisioned capacity

### EBS Snapshot 
- Make a backup (snapshot) of your EBS volume at a point in time
- Not necessary to detach volume to do snapshot, but recommended
- Can copy snapshot and convert to different AZ or region

### practice :
1. create a new volume and attach the volume to the instance
- volumes with different Availability Zones cannot be added
2. stop the instance and see if the volume is still there or not
3. Take a snapshot of the volume
4. Create a volume from a snapshot and attach it to a different Availability Zone
5. restore deleted snapshot with recycle bin

## AMI (Amazon Machine Image)
AMI is a template that contains software, configuration, operating system, monitoring, etc. that is used to launch your instance. AMI is built for a specific region but can be copied to different regions.
The AMIs we can use to launch EC2 instances are :
- A Public AMI: AWS provided
- Your own AMI: you make and maintain them yourself
- An AWS Marketplace AMI: an AMI someone else made (and potentially sells)

### practice :
- create an AMI from an instance
- create an instance of the AMI that we created earlier


## Social Proof

[Twitter](https://mobile.twitter.com/tiaradwim1306/status/1612752359867944961)
