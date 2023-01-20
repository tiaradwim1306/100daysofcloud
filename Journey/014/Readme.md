
# Deployment & Managing Infrastructure Part 1 : Course on Udemmy by Stepahane Mareek


## Cloud Research
### CloudFormation 
CloudFormation is a service that is used to manage existing resources as desired, for example you want:
- I want a security group
- I want two EC2 instances using this security group
- I want an S3 bucket
- I want a load balancer (ELB) in front of these machines

Then CloudFormation builds them for you, in the right order, with the exact configurations you specify

Benefits of AWS CloudFormation :
- Infrastructure as code
- cost 
- productivity
- take advantage of templates and documentation as well
- support (almost) all AWS resources 

### CDK (Cloud Development Kit)
This service is useful if you want to define your infrastructure with programming languages, for example JavaScript, Python, Java, etc.

ex : CDK - CDK CLI - CloudFormation template - CloudFormation

from the CDK we use the CDK CLI to change other programming languages into CloudFormation templates which will be used later in CloudFormation

### Beanstalk
Elastic Beanstalk is a developer-centric deployment view the application on AWS.Beanstalk is free but you pay for the underlying instance
Beanstalk is PaaS (Platform as a Service)

- Elastic Beanstalk manages services like instance configuration, load balancing and auto scaling, etc.
- The developer is only responsible for the application code used




## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1616286971986612225)
