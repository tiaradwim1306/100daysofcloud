
# Deployment & Managing Infrastructure Part 2 : Course on Udemmy by Stepahane Mareek

## Cloud Research
### AWS CodeDeploy
Hybrid service to deploy applications automatically and upgrade it from version 1 to version 2, working with EC2 instances and on-promises servers.
must provide a server that has CodeDeploy installed first.

### AWS CodeCommit 
Developers pushing code for applications in repositories with Git technology for example GitHub , but on AWS there is also the same product is CodeCommit.
CodeCommit Makes it easy to collaborate with others on code and code changes are automatically versioned.
benefits :
- Fully managed
- Scalable & highly available
- Private, Secured, Integrated with AWS

### AWS CodeBuild
Code building service in the cloud and compiles source code, run tests, and produces packages that are ready to be deployed 
benefits :
- Fully managed, serverless
- Continuously scalable & highly available
- Secure
- Pay-as-you-go pricing – only pay for the build time

### CodePipeline
Service for orchestrate the different steps to have the code automatically pushed to production. This service ensures that services like CodeCommit, CodeBuild, CodeDeploy get to Elastic Beanstalk

Process :
Code -> Build -> Test -> Provision -> Deploy

benefits :
- Fully managed, compatible with CodeCommit, CodeBuild, CodeDeploy, Elastic Beanstalk, CloudFormation, GitHub, 3rd-party services (GitHub…) & custom plugins…
- Fast delivery & rapid updates

### AWS CodeArtifact
- Software packages depend on each other to be built (also called dependency code), and new ones are created
- Usually you need to set up your own artifact management system, now you can use CodeArtifact for secure, scalable and cost-effective artifact management for software development.

### AWS CodeStar
easy way to easily manage your software development activities in one place, here you can start setting up CodeCommit, CodePipeline, CodeBuild, CodeDeploy, Elastic Beanstalk, EC2, etc…

### Cloud9
- AWS Cloud9 is a cloud IDE (Integrated Development Environment) for writing, running, and debugging code
- like IntelliJ, Visual Studio Code that you download on your computer before use but the IDE is used in a web browser that you can manage anywhere.
- AWS Cloud9 also enables code collaboration in real-time (pair programming)

### AWS Systems Manager (SSM)
- Another Hybrid AWS service for Helps you manage your EC2 and On-Premises systems at scale
- Get operational insights about the state of your infrastructure

How Systems Manager works
- We need to install the SSM agent onto the systems we control
- Installed by default on Amazon Linux AMI & some Ubuntu AMI
- If an instance can’t be controlled with SSM, it’s probably an issue with the SSM agent!
- Thanks to the SSM agent, we can run commands, patch & configure our servers

### AWS OpsWorks
- Chef & Puppet help you perform server configuration automatically, or repetitive actions
- They work great with EC2 & On-Premises VM
- AWS OpsWorks = Managed Chef & Puppet
- It’s an alternative to AWS SSM
- Only provision standard AWS resources like EC2 Instances, Databases, Load Balancers, EBS volumes…

### summary 
- CodeCommit: Store code in private git repository (version controlled)
- CodeBuild: Build & test code in AWS
- CodeDeploy: Deploy code onto servers
- CodePipeline: Orchestration of pipeline (from code to build to deploy)
- CodeArtifact: Store software packages / dependencies on AWS
- CodeStar: Unified view for allowing developers to do CICD and code
- Cloud9: Cloud IDE (Integrated Development Environment) with collab
- AWS CDK: Define your cloud infrastructure using a programming language

## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1616292538327117824)
