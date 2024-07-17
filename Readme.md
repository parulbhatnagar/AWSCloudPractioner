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