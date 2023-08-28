<h1>AWS WordPress Website</h1>

<h2>Description</h2>
This project involves deploying and hosting a WordPress website on the Amazon Web Services (AWS) platform. WordPress is a popular content management system (CMS) used for creating and managing websites. By leveraging AWS services, the project aims to provide a scalable, secure, and highly available infrastructure for the WordPress website<br />


<h2> Key Components and Technologies:</h2>

1. Amazon EC2: Amazon Elastic Compute Cloud (EC2) is used to provision virtual servers, known as EC2 instances, to host the WordPress application. EC2 instances provide the necessary compute resources to run the website.

2. Amazon RDS: Amazon Relational Database Service (RDS) is used to set up and manage a MySQL or Aurora database for storing the website's content, settings, and user data. RDS provides a scalable and managed database solution.

3. Amazon S3: Amazon Simple Storage Service (S3) is used to store media files, such as images and videos, used in the WordPress website. S3 provides scalable and durable object storage.

4. Amazon CloudFront: CloudFront is a content delivery network (CDN) service provided by AWS. It is used to distribute the website's static assets, such as CSS, JavaScript, and images, globally, reducing latency and improving performance.

5. Amazon Route 53: Route 53 is a scalable and highly available domain name system (DNS) service provided by AWS. It is used to route incoming requests to the WordPress website's EC2 instances or CloudFront distribution.

6. Amazon Certificate Manager (ACM): ACM is used to provision and manage SSL/TLS certificates for securing the website with HTTPS. ACM provides free SSL certificates that can be easily integrated with other AWS services.

7. AWS Identity and Access Management (IAM): IAM is used to manage access and permissions for AWS resources. It allows you to create and manage users, groups, and roles with fine-grained access control.

<h2>Project Workflow:</h2>
1. Design the architecture: Define the components and services required for the website, including VPC, Internet Gateways, NAT Gateways, EC2 Instances, RDS Database, and EFS Filesystem.
<p align="center">
Serverless Architecture: <br/>
<p align="center">
<img src="https://imgur.com/H6KgRA1.png" height="80%" width="80%">
<br />

2. The first step of this architecture would be to select the region where we want to deploy this website. On the top right corner, select the appropriate region you are at. The next step is to create your VPC. On the AWS Management Console, Navigate to VPC. Click on Create VPC. For the purpose of this project will give it a CIDR Block of 10.0.0.0/16. You can choose any CIDR block you want.
<p align="center">
<img src="https://imgur.com/TU0sbmb.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/Ot4UizW.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/Ot4UizW.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/gj63j1f.png" height="80%" width="80%">
<br />

3. For the instances in our Subnets to have access to the internet, we need to create an Internet Gateway. On the Left side on the VPC main page, Scroll down to the Internet Gateways option. Click on Create Internet Gateway. Attach it to the VPC you just created.
<p align="center">
<img src="https://imgur.com/tTWyBQ0.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/njWYPKd.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/fDhl4F6.png" height="80%" width="80%">
<br />

4. Next we will create Subnets in our VPC. First we will create Public Subnets. We require two Public Subnets, One in the Availibility Zone 1a and the other in the Availability zone 1b. Make sure to enable the auto assign IP address in the IP Settings.
<p align="center">
<img src="https://imgur.com/aTiWajA.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/qvRZbAZ.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/6mQfagY.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/hUhisQ1.png" height="80%" width="80%">
<br />
  
  
  
  
  4. Install and configure WordPress: Download and install the WordPress CMS on the EC2 instances. Configure the database connection settings to connect to the RDS instance.

5. Set up S3 bucket: Create an S3 bucket to store media files used in the WordPress website. Configure the necessary permissions and access control for the bucket.

6. Configure CloudFront: Set up a CloudFront distribution to serve the website's static assets, such as CSS, JavaScript, and images. Configure the CloudFront distribution to use the S3 bucket as the origin.

7. Configure Route 53: Set up DNS records in Route 53 to route incoming requests to the WordPress website's EC2 instances or CloudFront distribution.

8. Enable HTTPS: Use ACM to provision an SSL/TLS certificate for the website's domain. Configure the web server to enable HTTPS and redirect HTTP traffic to HTTPS.

9. Set up backups and monitoring: Configure regular backups for the RDS database and implement monitoring and logging using AWS CloudWatch to track and analyze website performance and health.

<h2>Benefits of AWS WordPress Website:</h2>

- Scalability: AWS allows you to scale the infrastructure resources, such as EC2 instances and RDS databases, based on website traffic and demand, ensuring optimal performance.
- High availability: By leveraging multiple availability zones and load balancing, AWS provides high availability for the WordPress website, minimizing downtime and ensuring continuous access.
- Security: AWS offers various security features, such as IAM for access control, ACM for SSL/TLS certificates, and VPC for network isolation, to enhance the security of the WordPress website.
- Cost-effectiveness: AWS provides a pay-as-you-go pricing model, allowing you to optimize costs by scaling resources as needed and only paying for the actual usage.
<h2>Project Workflow:</h2>
