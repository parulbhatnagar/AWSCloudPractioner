# _AWS Cloud Practitioner Essential Course_

# Module 1

## Cloud computing
The on-demand delivery of IT Resources over the internet with pay-as-you-go pricing


## Different Service

### Amazon Elastic Compute Cloud (Amazon EC2)
Virtual servers called EC2 instance

#### Amazon EC2 instance families
1. General Purpose
2. Compute optimized
3. Memory optimized
4. Accelerated computing
5. Storage optimized


#### Scaling and Availability service

EC2 can be scaled vertically by resizing 
EC2 can be scaled horizontally by launching new pool


**Amazon EC2 Auto scaling** - Automated horizontal scaling
**Elastic Load Balancing (ELB)** - Distribution of request across horizontally scaled instances


#### EC2 billing options

1. On-demand, which is the most flexible and has no contract. 
2. Spot pricing, which allows you to utilize unused capacity at a discounted rate. 
3. Savings plans or reserved instances, which allow you to enter into a contract with AWS to get a discounted rate when you commit to a certain level of usage 
4. Dedicated instance Savings plans which apply to AWS Lambda and AWS Fargate, as well as EC2 instances.


#### Messaging service
**Amazon Simple Queue Service (Amazon SQS)** - This service allows you to decouple system components. Messages remain in the queue until they are either consumed or deleted. 
**Amazon Simple Notification Service(Amazon ANS)** -  is used for sending messages like emails, text messages, push notifications or even HTTP requests. Once a message is published, it is sent to all the subscribers.


#### types of compute services

AWS has different types of compute services beyond just virtual servers like EC2, container orchestration tools, You can use these tools with EC2 instances
**Amazon Elastic Container Service or ECS**

**Amazon Elastic Kubernetes Service or EKS**


**Serverless computing**
 You can use **AWS Fargate**, which allows you to run your containers on top of a serverless compute platform. 

Then there is **AWS Lambda**, which allows you to just upload your code and configure it to run based on triggers. You only get charged for when the code is actually running, no containers, no virtual machines, just code and configuration. 


# Module 2

## AWS Global Infra an reliability

Goal is to be highly available and Fault tolerant.

### Regions
**Regions** are geographically isolated areas.

Data never leaves region unless you ask for.

Four factors to choose Region
1. Compliance
2. Proximity to user
3. Feature Availability
4. Pricing

### Availability Zones (AZ)
Region contains **Availability Zones(AZ)** _seperated bey 10 of miles from each other_

Choose multiple Availability zones for your app.

Recommendation is to choose multiple EC2s  within a region but in different availability zones.

### Amazon Cloud Front service
**Edge Locations** run **Amazon Cloud Front** (_Content Delivery Network Cached copy near user_) 

## Provisioning of AWS Resources

Everything is API's in AWS

### Ways to interact
1. AWS Management console - _UI_
2. AWS Command Line Interface - _commandline for scripting_
3. Software development kits (SDKs) - _integration with programs in different programming languages_
4. Managed tools 
   1. **AWS Elastic Beanstalk** -you provide code and configuration settings, and Elastic Beanstalk deploys the resources necessary to perform the following tasks 
      1. Adjust capacity 
      2. Load balancing 
      3. Automatic scaling 
      4. Application health monitoring
      
   2. Software development kits (SDKs) - you can treat your infrastructure as code, json based / yaml , acts as input for Cloud formation engine. manages different resources like storage, database, analytics , machine learning etc.