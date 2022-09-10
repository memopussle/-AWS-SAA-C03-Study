<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#">Introduction - AWS Certified Solutions Architect Associate</a>
    </li>
     <li>
      <a href="#">IAM & AWS CLI</a>
      <ul>
      <li> <a href="#">IAM = Identity and Access Management, Global Service</a></li>
      </ul>
    </li>
    <li>
      <a href="#">EC2 Fundamentals</a>
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

# What's AWS?

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

### IAM = Identity and Access Management, Global Service

- Root account created by default, shouldn't be shared or used
- **Users** are people within your organization, and can be grouped
  -user doesn't have to belong to a group, and user can belong to multiple groups

![Availability zones](./img/group.png)

### IAM: Permissions

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
