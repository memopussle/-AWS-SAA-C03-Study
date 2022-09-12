<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#What-is-AWS?">Introduction - AWS Certified Solutions Architect Associate</a>
      <ul>
      <li><a href="#AWS-Cloud-Use-Cases">AWS Cloud Use Cases</a></li>
       <li><a href="#AWS-Global-Infrastructure">AWS Global Infrastructure</a></li>
      </ul>
    </li>
     <li>
      <a href="#">IAM & AWS CLI</a>
      <ul>
      <li> <a href="#IAM---Identity-and-Access-Management-Global-Service">IAM = Identity and Access Management, Global Service</a></li>
      <li><a href="#IAM---Permissions">IAM - Permissions</li>   
      <li><a href="#IAM-Policies">IAM Policies</li>   
      <li><a href="#IAM-MFA-Overview">IAM MFA Overview</li>   
      <li><a href="#How-can-users-access-AWS">How can users access AWS</li>   
      <li><a href="#IAM-Roles-for-Services">IAM Roles for Services</li>   
  <li><a href="#IAM-Section---Summary">IAM Section - Summary</li>      
      <li><a href="#IAM-Guidlines-and-Best-Practices">IAM Guidlines and Best Practices </li>      
      </ul>
    </li>
    <li>
      <a href="#">EC2 Fundamentals</a>
      <ul>
      <li><a href="#EC2-Basics">EC2 Basics</a></li>
      <li><a href="#EC2-Instance-Types-Basics">EC2 Instance Types Basics</a></li>
      <li><a href="#Security-Groups">Security Groups</a></li>
      <li><a href="#Classic-Ports-to-know">Classic Ports to know</a></li>
      <li><a href="#EC2-Instances-Purchasing-Options">EC2 Instances Purchasing Options</a></li>
      <li><a href="#Spot-Fleets">Spot Fleets</a></li>
      </ul>
    </li>
     <li>
      <a href="#">EC2 - Solutions Architect Associate Level</a>
    </li>
     <li>
      <a href="#">EC2 Instance Storage</a>
    </li>
     <li>
      <a href="#">High availability and Scalability</a>
    </li>
     <li>
      <a href="#">AWS Fundamentals: RDS + Aurora + ElastiCache</a>
    </li>
     <li>
      <a href="#">Route 53</a>
    </li>
     <li>
      <a href="#">Classic Solutions Architect Discussions</a>
    </li>
     <li>
      <a href="#">Amazon S3 Introduction</a>
    </li>
     <li>
      <a href="#">AWS SDK, IAM Roles & Policies</a>
    </li>
    <li>
      <a href="#">Advanced Amazon S3</a>
    </li>
    <li>
      <a href="#">CloudFront & AWS Global Accelerator</a>
    </li>
       <li>
      <a href="#">AWS Storage Extras</a>
    </li>
  </ol>
</details>

# What is AWS?

- AWS (Amazon Web Services) is a Cloud Provider
- Provide you with servers and services that you can use **on demand** and **scale easily**
- AWS powers some of the biggest websites in the world

## AWS Cloud Use Cases

1.  AWS enables you to build sophisticated, scalable applications
2.  Applicable to a diverse set of industries
3.  Use cases include:

- Enterprises IT, Backup & Storage, Big Data analytics
- Website hosting, Mobile & Social Apps
- Gaming

## AWS Global Infrastructure

<ol>
  <li>
  <p> AWS Regions</p>
  <ul>
  <li>All around the world</li>
    <li>A region is a cluster of data centers</li>
    <li>How to choose an AWS Region?</li>
    <ul>
    <li>
    Compliance with data governance and lega requirementsL region
    </li>
    <li>Proxmity to customers: ex Customer are in US -> choose US region. Reduce lags</li>
     <li>Available services within a Region: New servuces and new features aren't available in every Region</li>
      <li>Pricing: varies region to region and is transparen in the service pricing page</li>
    </ul>
  </ul>
  </li>
  <li><p>AWS Availability Zones</p>

![Availability zones](./img/avail-zones.png)

   <ul>
   <li>Each region has many availability zones ( usually 3, min is 2, max is 6). ex: ap-southeast-2a, ap-southeast-2b, ap-southeast-2c</li>
   <li>Each availability zone (AZ) is one or more discrete data centers with redundant power, networking, and connectivity </li>
   <li>They're seperate from each other, so that they're isolated from disasters</li>
   <li>Connected with high bandwidth, ultra-low latency networking</li>
  
   </ul>  
  </li>
  <li>AWS Data Centers</li>
  <li>AWS Edge Locations / Points of Presence
  <ul>
  <li>Amazon has 216 Points of Presence (205 Edge Locations & 11 Regional Cache) in 84 cities accross 42 countries</li>
   <li>Content is delivered to end user with lower latency</li>
  </ul>
  </li>
  <li>Tour of the AWS Console
  <ul>
  <li>AWS has Global Services
  <ul>
  <li>Identity and Access Management (IAM)</li>
   <li>Route 53 (DNS service)</li>
    <li>CloudFront (Conten Delivery Network)</li>
    <li>WAF (Web Application Firewall)</li>
  </ul>
  </li>
  <li>Most AWS services are Region-scoped:
  <ul>
  <li>Amazon EC2 (Infrastructure as a Service)</li>
   <li>Elastic Beanstalk (Platform as a Service)</li>
    <li>Lambda (Function as a Service)</li>
    <li>Rekonigtion (Software as a Service)</li>
  </ul>
  </ul>
  </li>
</ol>

# IAM: Users & Groups

### IAM - Identity and Access Management, Global Service

- Root account created by default, shouldn't be shared or used
- **Users** are people within your organization, and can be grouped
  -user doesn't have to belong to a group, and user can belong to multiple groups

![Availability zones](./img/group.png)

### IAM - Permissions

- **Users or Groups** can be assigned JSON documents called policies
- These poloces define the permissiones of the users
- In AWS you apply the least priviledge principle: don't give more permissions than a user needs
  ![Availability zones](./img/poliy.png)

### IAM Policies

![Policies Inheritance](./img/policies-inheritance.png)

-Alice, Bob, Charles inherit a specific policy

- David, Edward inherit a specific policy
- Fred doesn't belong to any group -> own policy
- Charles & David: Share same audit policy and each person inherit each team's policy

### IAM Policies Structure

![Policies Inheritance](./img/iam-policy-structure.png)
Consist of:

<ul>
<li>
Version: policy language version, always include 2012-10-17
</li>
<li>
Id: an identifier for the policy (optional)
</li>
<li>
Statement: one ormore individual statements (required)
<ul>
Statements has:
<li>
Sid: an identifier for the statement (optional)
</li>
<li>
Effect: whether statement allows or denies access (Allow, Deny)
</li>
<li>
Principal: account/user/role to which policy applied to 
</li>
<li>
Action: list of actions this policy allows or denies
</li>
<li>
Resource: list of resources to which the actions applied to
</li>
<li>
Condition: conditions for when this policy is in effect (optional)
</li>
</ul>
</li>

</ul>

### IAM MFA Overview

 <ul>
 <li>
 Strong passwords = higher security for your account

 </li>
 <li>
 In AWS, you can setup a password policy: </li>
 <ul>
 <li>Set a minimum password length</li>
 </li>Require specific character types</li>
 </li>
 <ul>
 <li>uppercase letters</li>
 <li>lowercase letters</li>
 <li>numbers</li>
 <li>non-alphanumeric characters</li>

 </ul>
 </li>
 </ul>
 </li>
 <li>Allow all IAM users to change their own passwords</li>
 <li>Require users to change their password after some time (password expiration)</li>
 <li>Prevent password re-use</li>
 </ul>

### Multi Factor Authentication - MFA

- Users have access to your account and can possibly change configurations or delete sources in your AWS account
- **You want to protect your Root Accounts and IAM users**
- MFA = password you know + security device you own

  ![Policies Inheritance](./img/mfa.png)

- Main benefit of MFA:
  _if a password is stolen or hacked, the account is not compromised_

### MFA devices options in AWS

![Policies Inheritance](./img/deviceoptions.png)

![Policies Inheritance](./img/2nddeviceoptions.png)

### How can users access AWS

- To Access AWS, you have 3 options
<ul>
<ul>
<li> AWS Management Console (protected by password + MFA)
</li>
<li>
AWS Command Line Interface (CLI): protected by access keys
</li>
<li>
AWS Software Developer Kit (SDK): - for code: protected by access keys
</li>

</ul>
</ul>

- Access keys are generated through AWS Console
- Users manage their own access keys
- Access Key are secret, just like a password. Don't share them
- Access Key ID ~= username
- Secret Access key ~= password

![Policies Inheritance](./img/example-access-keys.png)

### What's the AWS CLI

- A tool that enables you to interact with AWS services using commands in your command-line shell
- Direct access to the public APIs of AWS services
- You can develop scripts to manage your resources
- It's open-source https://github.com/aws-cli
- Alternative to using AWS Management Console

![Policies Inheritance](./img/aws-cli.png)

### What's AWS SDK?

- AWS Software Development Kit (AWS SDK)
- Language-specific APIs (set of libraries)
- Enables you to access and manage AWS services programmatically
- Embedded with your application
- Supports
  - SDKs (JavaScript, Python, PHP,.NET, Ruby, Java, Go, Nodejs, C++)
  - Mobile SDKs (Android, iOS,...)
  - IOT Device SDKs (Embedded C, Arduino...)
- Exampe: AWS CLI is built on AWS SDK for Python

### AWS Cloud Shell

- A terminal in AWS

![AWS Cloud Shell](./img/aws-cloudshell.png)

### IAM Roles for Services

- Some AWS Service will need to perform actions on your behalf
- To do so, we will assign **permission** to AWS services with IAM roles

- Common roles:
  - EC2 Instance Roles
  - Lambda Function roles
  - Roles for CloudFormation

### IAM Security Tools

- IAM Credentials Report (account-level)

  - A report that lists all your account's users and the status of their various credentials

- IAM Access Advisor (user-level)
  - Access advisor shows the service permissions granted to a user and when those services were last accessed.
  - You can use this information to revise your policies

### IAM Guidlines and Best Practices

- Don't use the root accout except for AWS account setup
- One physical user = One AWS user
- **Assign users to groups** and assign permissions groups (to manage at group level)
- Create a **strong password policy**
- Use and enforce the use of Multi Factor Authentication (MFA)
- Create and use Roles for giving permissions to AWS services
- Use Access Keys for Programmatic Access (CLI/SDK)
- Adit permissions of your account with the IAM Credentials Report
- NEVER share IAM users & Access Keys
  ![AWS Cloud Shell](./img/credential-repor.png)

### IAM Section - Summary

- **Users**: Mapped to a physical user, has a password for AWS Console
- **Groups**: contains users only
- **Policies**: JSON document that outlines permissions for users or groups
- **Roles**: for EC2 intances or AWS services
- **Security**: MFA + Password Policy
- **Access keys**: Access AWS using the CLI or SDK
- **Audit**: IAM Credential Reports & IAM Access Advisor

# EC2 Fundamentals

### EC2 Basics
- EC2 is one of the most popular of AWS offering
- EC2: Elastic Compute Cloud = Infrastructure as a Service
- It mainly consists in the capability of:
  + Renting virtual machines (EC2)
  + Storing data on virtual drives (EBS)
  + Distributing load accross machines (ELB)
  + Scaling the services using an auto-scaling group (ASG)

- Knowing EC2 is fundamental to understand how the Cloud works

### EC2 Instance Types Basics

#### EC2 Instance Types - Overview
- You can use different types of EC2 instances that are optimised for different use cases (check out instances type in Amazon)
- AWS has the following naming convention: m5.2xlarge 
  + m: instance class
  + 5: generation (AWS improves them over time. next time it will be m6)
  + 2xlarge: size within the instance class (the more the size, the larger in size it will be)

  #### EC2 Instance types - General Purpose
  - Great for a diversity of workloads such as web servers or code repositories 
  - Balance between: 
    + Compute
    + Memory
    + Networking 
  - In the course, we will be using t2.mico which is a General Purpose EC2 instance
    ![AWS Cloud Shell](./img/ec2-instance.png)
  
#### EC2 Instance Types - Compute Optimized (Instances start with C. C: Compute)
- Great for compute-intensive tasks that require high performance processors:
 + Batch processing workloads
 + Media transcoding
 + High performance web servers
 + High performance computing (HPC)
 + Scientific modeling & machine learning
 + Dedicated gaming servers

  ![AWS Cloud Shell](./img/ec2-computeoptimized.png)
   
#### Instance Types - Memory Optimized (Instances start with R. R: Ram)
- Fast performance for workloads that process large data sets in memory 
- Use cases:
  + High performance, relational/non-relational databases
  + Ditributes web scale cache stores
  + In-memory databases optimized for BI (business intelligence)
  + Applications performing real-time processing of big unstructured data

  ![AWS Cloud Shell](./img/memory-instances.png)

#### EC2 Instance Types - Storage Optimized (Instances start with I or D)
- Great for storage-intensive tasks that require high, sequential read and write access to large sets on local storage
- Use cases:
  + High frequency online trancsaction processing (OLTP) systems
  + Relational & NoSQL databases
  + Cache for in-memory databases (for example, Redis)
  + Data warehousing applications
  + Distributed file systems

  ![AWS Cloud Shell](./img/storage-instances.png)

#### EC2 Instance Types: example comparison


  ![AWS Cloud Shell](./img/ec2-instances-comparison.png)

  -> ec2instances.info (to see the ec2 instances comparison in full)

### Security Groups
- Security Groups are fundamental of network security in AWS
- They control how traffic is allowed into or out of our EC2 Instances
- Security groups only contain allow rules
- Security groups rules can reference by IP or by security group


  ![AWS Cloud Shell](./img/security-groups.png)
### Security Groups Deeper Dive
- Security groups are acting as a "firewall" on EC2 instances
- They regulate:
    + Access to ports
    + Authorised IP ranges - IPv4 and IPv6
    + Control of inbound network (from other to the instance)
    + Control of outbound network (from the instance to other)

  ![AWS Cloud Shell](./img/security-groups-deeper-dive.png)

  ![AWS Cloud Shell](./img/security-diagram.png)
    
  ### Security Groups - Good to know
  - Can be attached to multiple instances
  - Locked down to a region / VPC combination (if change region, has to set up security group again)
  - Does live "outside" the EC2 - if traffic is blocked the EC2 instance won't see it
  - It's good to maintain one seperate security group for SSH access
  - If your application is not accessible (time out), then it's a security group issue
  - If your application gives "connection refused" error, then it's an application error or it's not launched.
  - All inbound traffic is blocked by default
  - All outbound traffic is authorised by default

   ![AWS Cloud Shell](./img/how-security-groups-work.png)

   ### Classic Ports to know
   - 22 = SSH (Secure Shell) - log into a Linux instance
   - 21 = FTP (File Transfer Protocol) - upload files into a file share
   - 22 = SFTP (Secure File Trasnfer Protocol) - upload files using SSH 
   - 80 = HTTP - access unsecured websites
   - 443 = HTTPS - access secured websites
   - 3389 = RDP (Remote Desktop Protocol) - log into a Window instance

   ### SSH Summary Table

      ![AWS Cloud Shell](./img/ssh-summary-table.png)

1. Connect SSH with command lines
    ![AWS Cloud Shell](./img/cli-ssh.png)

   - Allows you to controll remote machine, all using the command line. 

  - To install, open terminal and:
   ```sh
   ssh -i .\project_name.pem ec2-user@Public_IPv4_address 
   ```
  
2. Connect SSH with EC2 instances (using cli interfact inside aws)

- Attach IAM roles for the intances ( IAMReadOnly), rather than do configuration by yourself (another user can steal it, s for security reasons). We assign IAM roles (IAMReadOnlyAccess) to the Instances, now aws cli , do ```aws iam list-users```, we will get access to the user

### EC2 Instances Purchasing Options
- On-demands Instances - short workload, predictable pricing, pay by second
- Reserved ( 1 & 3 years)
  + Reserved Instances - long workloads
  + Convertible Reserved Instances - long workloads with flexible instances
- Saving plans (1 & 3 years) - commitment to an amount of usage, long workload
- Spot Instances - short workloads, cheap, can lose instances (less reliable)
- Dedicated Hosts - book an entire physica server, control instance placement
- Dedicated Instances - no other customers will share your hardware
- Capacity Reservations - reserve capacity in a specific AZ for any durations

<table>
  <tr>
    <th>On-demands Instances</th>
    <td>Short workload, predictable pricing, pay by second</td>
  </tr>
  <tr>
    <th>Saving plans</th>
    <td>Commitment to an amount of usage, long workload</td>
  </tr>
    <tr>
    <th>Spot Instances</th>
    <td>short workloads, cheap, can lose instances (less reliable)</td>
  </tr>
   <tr>
    <th>Dedicated Hosts</th>
    <td>book an entire physica server, control instance placement</td>
  </tr>
   <tr>
    <th> Dedicated Instances</th>
    <td> no other customers will share your hardware</td>
  </tr>
    <tr>
    <th> Capacity Reservations</th>
    <td> reserve capacity in a specific AZ for any durations</td>
  </tr>
</table>

#### EC2 On Demand
- Pay for what you use:
  + Linux or Windows - billing per second, after the first minute
  + All other operating systems - billing per hour

- Has the highest cost but no upfront payment 
- No long-term commitment

- Recommended for **short-term** and **un-interrupted workloads**, where you can't predict how the application will behave

### EC2 Reserved Instances
- Up to 72% discount compared to On-demand
- You reserve a specific instance attributes (Instance Type, Region, Tenancy, OS)
- Reservation Period - 1 year (+discount) or 3 years (+++discount)
- Payment Options - No Upfront (+), Partial Upfront(++), All Upfront (+++)
- Reserved Instance's Scope - Regional or Zonal (reserve capacity in an AZ)
- Recommended for steady-state usage applications (think database)
- You can buy and sell in the Reserved Instance Marketplace

- Convertible Reserved Instance
  + Can change the EC2 instance type, instance family, OS, scope and tenancy
  + Up to 66% discount


### EC2 Saving Plans
- Get a discount based on long-term usage (up to 72% - same as RIs)
- Commit to a certain type of usage ($10/hour for 1 or 3 years)
- Usage beyond EC2 savings plans is billed at the On-Demand Price
- Locked to a specific instance family & AWS region (e.g M5 in us-east-I)
- Flexbile across:
  + Instance Size (e.g, m5.xlarge, m5.2xlarge)
  + OS (e.g Linux, Windows)
  + Tenancy (Host, Dedicated, Default)

### EC2 Spot Instances

- Can get a discount of up to 90% compared to On-demand
- Instances that you can "lose" at any point of time if your max price is less than the current spot price
- The Most cost-efficient instances in AWS
- Useful for workloads that are resilient to failure:
  + Batch jobs 
  + Data analysis
  + Any distributed workloads
  + Workloads with a flexible start and end time

- **Not suitable for critical jobs or databases**

#### EC2 Dedicated Hosts
- A physical server with EC2 instance capacity fully dedicated to your use
- Allows you address compliance requirements and use your existing server-bound software licenses (per-socket, per-core, pe-VM software licenses)
- Purchasing Options:
  + On-demand - pay per second for active Dedicated Host
  + Reserved - 1 or 3 years
- The most expensive option 
- Useful for software that have complicated licensing model (BYO: - Bring Your Own License)
- Or for companies that have strong regulatory or compliance needs

#### EC2 Dedicated Instances

- Instances run on hardware that's dedicated to you
- May share hardware with other instances in same account
- No control over instance placement (can move hardware after Stop/Start)

![AWS Cloud Shell](./img/ec2-dedicated-instances.png)

#### EC2 Capacity Reservations

- Reserve On-Demand instances capacity in a specific AZ for any duration
- You always have access to EC2 capacity when you need it
- **No time commitment** (create/cancel anytime), no billing discounts
- Combine with Regional Reserved Instances and Saving Plans to benefit from billing discounts
- You're charged at On-Demand rate whether you run instances or not
**Suitable for short-term, uninterrupted  workloads that needs to be in a specific AZ**

### Which options - EC2 pricing options

![AWS Cloud Shell](./img/example-ec2-purchasing-options.png)

![AWS Cloud Shell](./img/price-comparison-ec2.png)

### EC2 Spot Instance Requests (note: AWS won't be supported after December 31 2022. But it might appear in the exam)

- Can get discount of up to 90% compared to On-demand
- Define max spot price and get the instance while current spot price < max
  + The hourly spot price varies based on offer and capacity
  + If the current spot price > your max price, you can choose to **stop** or **terminate** your instance with a 2minute grace period
- Other strategy: Spot Block
 + "block" spot instance during a specified time frame (1 to 6 hours) without interruptions
- **Used for batched jobs, data analysis, or workloads that are resilient to failures** 
- Not great for critical jobs or databases :(


![AWS Cloud Shell](./img/ec2-block-instances.png)

### Terminate Spot Instances

![AWS Cloud Shell](./img/terminate-spot-instances.png)

### Spot Fleets
- Spot Fleets = set of Spot Instances = (optional) On-Demand Instances
- The Spot Fleet will try to meet the target capacity with price constraints
  + Define possible launch pools: instance type (m5.large, OS, Availabilty Zone)
  + Can have multiple launch pools, so that the fleet can choose
  + Spot Fleet stops launching instances when reaching capacity or max cost
- Strategies to allocate Spot Instances:
  + lowestPrice: from the pool with the lowest price (cost optimization, short workload)
  + diversified: distributed across all pools (great for availability, long workloads)
  + capacityOptimized: pool with the optimal capacity for the number of instances

  **Spot Fleets allows us to automatically request Spot Instances with the lowest price**

#### Difference Spot Fleets vs Block Instance

| Block Instance | Second Header |
| ------------- | ------------- |
| you place a bid for a specific instance type in one specific AZ and hope you get it |You can request a variety of different instance types that meet your requirements |


