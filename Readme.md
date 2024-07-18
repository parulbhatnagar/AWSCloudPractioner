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


# Module 3

## Networking

Amazon Virtual Private Cloud (VPC) -  A VPC lets you provision a logically isolated section of the AWS cloud where you can launch AWS resources in a virtual network that you define

Public anf private grouping of resource is called **subnets**

### Connectivity to AWS

#### Amazon Virtual Private Cloud (Amazon VPC)
magine the millions of customers who use AWS services. Also, imagine the millions of resources that these customers have created, such as Amazon EC2 instances. Without boundaries around all of these resources, network traffic would be able to flow between them unrestricted. 

A networking service that you can use to establish boundaries around your AWS resources is Amazon VPC.

#### Internet gateway
To allow public traffic from the internet to access your VPC, you attach an internet gateway to the VPC.
![img.png](src/images/img.png)

#### Virtual Private Gateway
The virtual private gateway is the component that allows protected internet traffic to enter into the VPC.
![img_1.png](src/images/img_1.png)

#### AWS Direct Connect
AWS Direct Connect is a service that enables you to establish a dedicated private connection between your data center and a VPC.
The private connection that AWS Direct Connect provides helps you to reduce network costs and increase the amount of bandwidth that can travel through your network
![img_2.png](src/images/img_2.png)

### Subnets and Network Access Control Lists
To learn more about the role of subnets within a VPC, review the following example from the coffee shop.

First, customers give their orders to the cashier. The cashier then passes the orders to the barista. This process allows the line to keep running smoothly as more customers come in.

Suppose that some customers try to skip the cashier line and give their orders directly to the barista. This disrupts the flow of traffic and results in customers accessing a part of the coffee shop that is restricted to them.

![img_3.png](src/images/img_3.png)


To fix this, the owners of the coffee shop divide the counter area by placing the cashier and the barista in separate workstations. The cashier’s workstation is public facing and designed to receive customers. The barista’s area is private. The barista can still receive orders from the cashier but not directly from customers.

![img_4.png](src/images/img_4.png)


This is similar to how you can use AWS networking services to isolate resources and determine exactly how network traffic flows.

In the coffee shop, you can think of the counter area as a **VPC**. The counter area divides into two separate areas for the cashier’s workstation and the barista’s workstation. In a VPC, subnets are separate areas that are used to group together resources.

#### Subnets
A subnet is a section of a VPC in which you can group resources based on security or operational needs. Subnets can be **public** or **private**.
![img_5.png](src/images/img_5.png)

**Public subnets** contain resources that need to be accessible by the public, such as an online store’s website.

**Private subnets** contain resources that should be accessible only through your private network, such as a database that contains customers’ personal information and order histories.

In a VPC, subnets can communicate with each other. For example, you might have an application that involves Amazon EC2 instances in a public subnet communicating with databases that are located in a private subnet.


#### Network Traffic in a VPC
When a customer requests data from an application hosted in the AWS Cloud, this request is sent as a packet. A packet is a unit of data sent over the internet or a network.

It enters into a VPC through an **internet gateway**. Before a packet can enter into a subnet or exit from a subnet, it checks for permissions. These permissions indicate who sent the packet and how the packet is trying to communicate with the resources in a subnet.

The VPC component that checks packet permissions for subnets is a **network access control list (ACL)**.

#### Network Access Control Lists (ACLs)
A network access control list (ACL) is a virtual firewall that controls inbound and outbound traffic at the subnet level.

For example, step outside the coffee shop and imagine that you are in an airport. In the airport, travelers are trying to enter into a different country. You can think of the travelers as packets and the passport control officer as a network ACL. The passport control officer checks travelers’ credentials when they are both entering and exiting out of the country. If a traveler is on an approved list, they are able to get through. However, if they are not on the approved list or are explicitly on a list of banned travelers, they cannot come in.
![img_6.png](src/images/img_6.png)

Each AWS account includes a default network ACL. When configuring your VPC, you can use your account’s default network ACL or create custom network ACLs.

By default, your account’s default network ACL allows all inbound and outbound traffic, but you can modify it by adding your own rules. For custom network ACLs, all inbound and outbound traffic is denied until you add rules to specify which traffic to allow. Additionally, all network ACLs have an explicit deny rule. This rule ensures that if a packet doesn’t match any of the other rules on the list, the packet is denied.

#### Stateless Packet Filtering
Network ACLs perform stateless packet filtering. They remember nothing and check packets that cross the subnet border each way: inbound and outbound.

Recall the previous example of a traveler who wants to enter into a different country. This is similar to sending a request out from an Amazon EC2 instance and to the internet.

When a packet response for that request comes back to the subnet, the network ACL does not remember your previous request. The network ACL checks the packet response against its list of rules to determine whether to allow or deny.

![img_7.png](src/images/img_7.png)

After a packet has entered a subnet, it must have its permissions evaluated for resources within the subnet, such as Amazon EC2 instances.

The VPC component that checks packet permissions for an Amazon EC2 instance is a **security group**.


#### Security Groups
A security group is a virtual firewall that controls inbound and outbound traffic for an Amazon EC2 instance.
![img_8.png](src/images/img_8.png)

By default, a security group denies all inbound traffic and allows all outbound traffic. You can add custom rules to configure which traffic to allow or deny.

For this example, suppose that you are in an apartment building with a door attendant who greets guests in the lobby. You can think of the guests as packets and the door attendant as a security group. As guests arrive, the door attendant checks a list to ensure they can enter the building. However, the door attendant does not check the list again when guests are exiting the building

If you have multiple Amazon EC2 instances within a subnet, you can associate them with the same security group or use different security groups for each instance.


Stateful Packet Filtering
Security groups perform stateful packet filtering. They remember previous decisions made for incoming packets.

Consider the same example of sending a request out from an Amazon EC2 instance to the internet.

When a packet response for that request returns to the instance, the security group remembers your previous request. The security group allows the response to proceed, regardless of inbound security group rules.
![img_9.png](src/images/img_9.png)



Both network ACLs and security groups enable you to configure custom rules for the traffic in your VPC. As you continue to learn more about AWS security and networking, make sure to understand the differences between network ACLs and security groups.
![img_10.png](src/images/img_10.png)


### Global Networking

#### Domain Name System (DNS)
Translating a domain name to an IP address
![img_11.png](src/images/img_11.png)

#### Amazon Route 53

It is a DNS Web service. It gives a reliable way to route internet applications hosted on AWS. It also manages domain names, so we can register our app on it. Amazon Clount from (CDN) work together with Amazon Route 51 to deliver content.

![img_12.png](src/images/img_12.png)


# Module 4

## Storage and Databases

### Amazon Elastic Block Storage (Amazon EBS)
It is a service that provides block-level storage volumes that you can use with Amazon EC2 instances. If you stop or terminate an Amazon EC2 instance, all the data on the attached EBS volume remains available.

To create an EBS volume, you define the configuration (such as volume size and type) and provision it. After you create an EBS volume, it can attach to an Amazon EC2 instance.

Because EBS volumes are for data that needs to persist, it’s important to back up the data. You can take incremental backups of EBS volumes by creating Amazon EBS snapshots.

#### Amazon EBS Snapshots
It is an incremental backup. This means that the first backup taken of a volume copies all the data. For subsequent backups, only the blocks of data that have changed since the most recent snapshot are saved.

Incremental backups are different from full backups, in which all the data in a storage volume copies each time a backup occurs. The full backup includes data that has not changed since the most recent backup.
![img_13.png](src/images/img_13.png)


### Amazon Simple Storage Service (Amazon S3)

Object Storage, each object consists of data, metadata, and a key. The data might be an image, video, text document, or any other type of file. Metadata contains information about what the data is, how it is used, the object size, and so on. An object’s key is its unique identifier.
![img_14.png](src/images/img_14.png)

**Amazon S3** is a service that provides object-level storage. Amazon S3 stores data as objects in buckets.
Amazon S3 offers unlimited storage space. The maximum file size for an object in Amazon S3 is 5 TB.
When you upload a file to Amazon S3, you can set permissions to control visibility and access to it. You can also use the Amazon S3 versioning feature to track changes to your objects over time.

