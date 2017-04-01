# First Steps Amazon Web Services (AWS)

[<img src="https://images.unsplash.com/reserve/wBE2ADjQzK2ubCBMiy7T_DSC_0285.JPG?dpr=2&auto=format&fit=crop&w=767&h=511&q=80&cs=tinysrgb&crop=">](https://unsplash.com/photos/IT4Za_Q_dTA) https://unsplash.com/photos/IT4Za_Q_dTA

Amazon Web Services provide a 12-month free trial with a certain usage threshold. Let's jump into it and see what we can do with it.
The AWS Management Console provides different guides to get started. I started with a simple website.



## 📄 Table of contents



---

>"“If you decide that you’re going to do only the things you know are going to work, you’re going to leave a lot of opportunity on the table.”" - Jeff Bezos

---


## 1. Set up a user management
Firstly create an AWS account - simply follow the instructions on their homepage.

Next set up an "Identity and Access Management" (IAM) to create access keys and not being forced to use your own account credentials.
Use the [IAM console](https://console.aws.amazon.com/iam/) to add a new user and a new group.

>Tip: When logging in with the new user, be sure to use the password from your main account and not the set "console password" - since it isn't referring to your AWS Management Console password.

## 2. Create Buckets

>You can use Amazon Simple Storage Service (Amazon S3) to store all the content that makes up your static website, including HTML pages, images, CSS files, videos, and JavaScript files. Each file is stored in Amazon S3 as an object in a location called a bucket.

The buckets need to have the same name as your domain to be resolved properly.

To create the bucket use the [S3 console](https://console.aws.amazon.com/s3/).

## 3. Configure buckets
S3 delivers the files in the bucket to the web browsers as if they were hosted on a server. Permissions have to be granted to make the files accessible for everyone.

Use the [S3 console](https://console.aws.amazon.com/s3/) to change permissions and properties of the bucket.

**Logging** allows to track the number of visitors, that are accessing the website.
>There is no extra charge for enabling logging on a bucket; however, you will accrue charges to store the resulting log files in the bucket that you specify.

## 4. Deploy Website

Create and upload a Index and Custom Error document.
Use the [S3 console](https://console.aws.amazon.com/s3/) to upload your files to the bucket.
It is also possible to create folders in the bucket itself.

Configure your bucket as a website, so that files are served as if they were hosted on a web server.

**Redirecting**
By redirecting traffic from the www subdomain bucket to the root domain bucket, you can maintain a single version of your website files in Amazon S3 while still supporting both the root and www subdomain versions of your website's address.

**Test**
To see if the deployment was successful navigate to the provided URL.


## 5. Variation: Using your own domain name

Again: Before you pay to register a domain name, check that the domain name that you used when you created your buckets in Amazon S3 (as described in Step 1: Create the Buckets for Your Website) is available with a domain name registrar.

>A Domain Name System (DNS) web service routes visitors to websites by translating domain names (such as www.example.com) into the numeric IP addresses (such as 192.0.2.1) that computers use to connect to each other.

Use Amazon Route 53 as your DNS service, to associate a domain name with your website.

To do that us the [Route53 console](https://console.aws.amazon.com/route53/)

- a "hosted zone" allows you to handle your domain and subdomain management
- "record sets" re-direct route queries for your domain name to your S3 bucked

## 6. Addition: Speed up your Website with CloudFront

CloudFront simply provides CDN functionality.
>When a visitor requests a file from your website, the request is automatically redirected to a copy of the file at the nearest edge location, which results in faster download times than if the visitor had requested the content from a data center farther away

Use the [CloudFront console](https://console.aws.amazon.com/cloudfront/) to set up data centers around the world.

❗ Don't forget to update you **record sets** to point to the CloudFront distributions as well. ❗
This again is done in the [Route53 console](https://console.aws.amazon.com/route53/).






####


<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1d/AmazonWebservices_Logo.svg/2000px-AmazonWebservices_Logo.svg.png" alt="AWS logo"/>
Source https://commons.wikimedia.org/wiki/File:AmazonWebservices_Logo.svg

## Conclusion

The guide shows how easy it actually is to set up a static hosting site. It can be done in a few hours and provides a lot of features. This first tutorial already demonstrates the power of AWS. Every beginner can easily publish his first website without complex knowledge of how to set up a hosting structure. I'm pleased :)




## Useful links & credits
- [📄 "Hosting a static Website" - Amazon (guide)](https://aws.amazon.com/de/getting-started/projects/host-static-website/?c_1)

```
Please leave comments, feedback and suggestions as I am always trying to improve.
Share your thoughts - it's never been easier 😄
```

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->
