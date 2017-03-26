# Introduction Amazon Web Services (AWS)

[<img src="https://images.unsplash.com/photo-1484157737210-f58966446e05?dpr=2&auto=format&fit=crop&w=767&h=508&q=80&cs=tinysrgb&crop=">](https://unsplash.com/photos/WbIEX9Hq-EI) https://unsplash.com/photos/WbIEX9Hq-EI

During my web development learning experience I came stumbled very often over Amazon Web Services but never really understood what it's capabilities are. The following article contains the things I have learned from my research.

If you want to start learning more about AWS check out my provided links at the end. Unfortunately there is a lot of outdated or simple badly explained content on the web. Be sure to consolidate a good resource.


## 📄 Table of contents

<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [Introduction Amazon Web Services (AWS)](#introduction-amazon-web-services-aws)
  * [📄 Table of contents](#table-of-contents)
  * [What is AWS?](#what-is-aws)
  * [AWS Products](#aws-products)
      * [Compute and Networking Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-compute-network.html#compute-network-concepts)](#compute-and-networking-services-detailshttpdocsawsamazoncomgettingstartedlatestawsgsg-introgsg-aws-compute-networkhtmlcompute-network-concepts)
      * [Storage and Content Delivery Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-storage-cdn.html)](#storage-and-content-delivery-services-detailshttpdocsawsamazoncomgettingstartedlatestawsgsg-introgsg-aws-storage-cdnhtml)
      * [Security and Identity Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-security-identity.html)](#security-and-identity-services-detailshttpdocsawsamazoncomgettingstartedlatestawsgsg-introgsg-aws-security-identityhtml)
      * [Database Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-database.html)](#database-services-detailshttpdocsawsamazoncomgettingstartedlatestawsgsg-introgsg-aws-databasehtml)
      * [Analytics Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-analytics.html)](#analytics-services-detailshttpdocsawsamazoncomgettingstartedlatestawsgsg-introgsg-aws-analyticshtml)
      * [Application Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-app.html)](#application-services-detailshttpdocsawsamazoncomgettingstartedlatestawsgsg-introgsg-aws-apphtml)
      * [Management Tools [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-management.html)](#management-tools-detailshttpdocsawsamazoncomgettingstartedlatestawsgsg-introgsg-aws-managementhtml)
  * [How do I use it?](#how-do-i-use-it)
  * [Keypoints on AWS and what is good?](#keypoints-on-aws-and-what-is-good)
  * [Example Steps for deploying an app](#example-steps-for-deploying-an-app)
  * [Conclusion](#conclusion)
  * [Useful links & credits](#useful-links-credits)

<!-- tocstop -->



---

>"I believe you have to be willing to be misunderstood if you're going to innovate." - Jeff Bezos

---

## What is AWS?
As Amazon explains in their [documentation](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-intro.html):
>Amazon Web Services (AWS) provides on-demand computing resources and services in the cloud, with pay-as-you-go pricing. For example, you can run a server on AWS that you can log on to, configure, secure, and run just as you would a server that's sitting in front of you.

The whole concept builds on top of the cloud computing principle. It provides IT infrastructure and other services over the internet.

And it's commonly used for:
>- Store public or private data.
>- Host a static website. These websites use client-side technologies (such as HTML, CSS, and JavaScript) to display content that doesn't change frequently. A static website doesn't require server-side technologies (such as PHP and ASP.NET).
>- Host a dynamic website, or web app. These websites include classic three-tier applications, with web, application, and database tiers.
>- Support students or online training programs.
>- Process business and scientific data.
>- Handle peak loads.

## AWS Products

The following categories represent the core products of AWS.

#### Compute and Networking Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-compute-network.html#compute-network-concepts)

- Amazon EC2 (Provides virtual servers in the AWS cloud)
- Amazon VPC (Provides an isolated virtual network for your virtual servers)
- Elastic Load Balancing (Distributes network traffic across your set of virtual servers)
- Auto Scaling (Automatically scales your set of virtual servers based on changes in demand)
- Amazon Route 53 (Routes traffic to your domain name to a resource, such as a virtual server or a load balancer)
- AWS Lambda (Runs your code on virtual servers from Amazon EC2 in response to events)
- Amazon ECS (Provides Docker containers on virtual servers from Amazon EC2)

#### Storage and Content Delivery Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-storage-cdn.html)

- Amazon S3 (Scalable storage in the AWS cloud)
- CloudFront (A global content delivery network (CDN))
- Amazon EBS (Network attached storage volumes for your virtual servers)
- Amazon Glacier (Low-cost archival storage)


#### Security and Identity Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-security-identity.html)

- AWS Identity and Access Management (Manage user access to AWS resources through policies)
- AWS Directory Service (Manage user access to AWS through your existing Microsoft Active Directory, or a directory you create in the AWS cloud)

#### Database Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-database.html)

- Amazon RDS (Provides managed relational databases)
- Amazon Redshift (A fast, fully-managed, petabyte-scale data warehouse)
- Amazon DynamoDB (Provides managed NoSQL databases)
- Amazon ElastiCache (An in-memory caching service)


#### Analytics Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-analytics.html)

Amazon EMR (Amazon EMR) uses Hadoop, an open source framework, to manage and process data. Hadoop uses the MapReduce engine to distribute processing using a cluster.

- Amazon EMR (You identify the data source, specify the number and type of EC2 instances for the cluster and what software should be on them, and provide a MapReduce program or run interactive queries)

- AWS Data Pipeline (to regularly move and process data)

- Amazon Kinesis (real-time processing of streaming data at a massive scale)

- ❗Amazon ML  (use machine learning technology to obtain predictions for their applications using simple APIs. Amazon ML finds patterns in your existing data, creates machine learning models, and then uses those models to process new data and generate predictions) ❗

#### Application Services [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-app.html)

- Amazon AppStream (Host your streaming application in the AWS cloud and stream the input and output to your users' devices)
- Amazon CloudSearch (Add search to your website)
- Amazon Elastic Transcoder (Convert digital media into the formats required by your users' devices)
- Amazon SES (Send email from the cloud)
- Amazon SNS (Send or receive notifications from the cloud)
- Amazon SQS (Enable components in your application to store data in a queue to be retrieved other components)
- Amazon SWF (Coordinate tasks across the components of your application)


#### Management Tools [[Details]](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-management.html)

- Amazon CloudWatch (Monitor resources and applications)
- AWS CloudFormation (Provision your AWS resources using templates)
- AWS CloudTrail (Track the usage history for your AWS resources by logging AWS API calls)
- AWS Config (View the current and previous configuration of your AWS resources, and monitor changes to your AWS resources)
- AWS OpsWorks (Configure and manage the environment for your application, whether in the AWS cloud or your own data center)
- AWS Service Catalog (Distribute servers, databases, websites, and applications to users using AWS resources)


## How do I use it?

AWS can be accessed through:
- AWS Management Console
- AWS Command Line Interface (AWS CLI)
- Command Line Tools
- AWS Software Development Kits (SDK)
- Query APIs

There is a detailed guide on how to install and use each of these options in the documentation.

As you can see it takes a while to get familiar with each tool to get into some sort of workflow.

## Keypoints on AWS and what is good?
- Elastic pay-per-use infrastructure
- On demand resources
- Scalability
- Global infrastructure
- Reduced time to market
- Increased opportunities for innovation
- Enhanced security


## Example Steps for deploying an app
- Load balancer tier (eg Elastic Load Balancing)
- Web/app tier (eg EC2 AutoScaling Group)
- Caching tier (eg ElastiCache for Memcached)
- Database tier (eg Multi-AZ RDS)
- Static content (eg Amazon S3)
- Content Delivery (with Amazon CloudFront)



<img src="https://images.unsplash.com/photo-1455735459330-969b65c65b1c?dpr=2&auto=format&fit=crop&w=767&h=510&q=80&cs=tinysrgb&crop=" alt="apps" height="200"/>
https://unsplash.com/photos/BdQk6Qm3vAU

## Conclusion

AWS provides building blocks that you can assemble quickly to support any workload. With AWS, you’ll find a complete set of highly available services that are designed to work together to build scalable applications.

Diving into AWS requires you to understand their own keywords and concepts. There is really a whole cloud computing world waiting for you. I am eager to explore more, seeing that I steadly gains popularity.


## Useful links & credits
- [📹 "Getting Started with Amazon Web Services"  - CS50 (YouTube)](https://www.youtube.com/watch?v=VgzzHCukwpc&t=276s)
- [📄 "Introduction to AWS" - Slideshare (slides)](https://de.slideshare.net/AmazonWebServices/introduction-to-amazon-web-services-7708257)
- [📄 "Intro to AWS cloud" - Amazon (PDF)](https://d0.awsstatic.com/whitepapers/introduction-to-aws-cloud-economics-final.pdf)
- [📄 "Getting started with AWS" - Ashok Karale (article)](http://www.c-sharpcorner.com/article/introduction-to-aws-getting-started-with-aws-account/)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)
- [📄 "Begin"](afgafgadgads)

```
Please leave comments, feedback and suggestions as I am always trying to improve.
Share your thoughts - it's never been easier 😄
```

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
