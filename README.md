

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#introduction">Introduction - AWS Certified Solutions Architect Associate</a>
    </li>
     <li>
      <a href="#">IAM & AWS CLI</a>
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
2.  Applicable to a  diverse set of industries
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
  <li>AWS Edge Locations / Points of Presence</li>
</ol>





