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

5. Now lets create a Route Table. From the VPC console, Navigate to Route Tables option and click on Create Table. After creating the table, click on the table and scroll down to Routes section. Click on Edit Routes. Then Click on Add Routes and add a route for the instances to connect to the Internet Gateway.
<p align="center">
<img src="https://imgur.com/PliiZSW.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/g6HbTWl.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/rkNcaew.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/h2gaPM1.png" height="80%" width="80%">
<br />

6. Now lets associate the Public Subnets with the Public Route Table. Click on the Route Table, Click on Subnet Associations and add the subnets. 
<p align="center">
<img src="https://imgur.com/lUOAjr7.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/1OhgdNT.png" height="80%" width="80%">
<br />  

7. Similar to the Step 4, lets create Private Subnets. We need four Private Subnets. One in each Availability Zone for EC2 instances and Database.
<p align="center">
<img src="https://imgur.com/Vt9rYnX.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/sPREugv.png" height="80%" width="80%">
<br />  
<p align="center">
<img src="https://imgur.com/Nyw1oYg.png" height="80%" width="80%">
<br />

8. Similarly, lets create the Private Route Tables for Availability Zones US-East 1a and 1b.
<p align="center">
<img src="https://imgur.com/j6icWIR.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/WUavko3.png" height="80%" width="80%">
<br />  
<p align="center">
<img src="https://imgur.com/FLNIbDL.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/4kEfsom.png" height="80%" width="80%">
<br />  
<p align="center">
<img src="https://imgur.com/vBOHU51.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/cEhL0ft.png" height="80%" width="80%">
<br />  
<p align="center">
<img src="https://imgur.com/ZGrhzbG.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/JCdYvYr.png" height="80%" width="80%">
<br />

9. Lets create a NAT Gateway in Public Subnet 1 and Public Subnet 2 and allocate Elastic IP's. Edit the Route Tables and add the route to the NAT Gateway.
<p align="center">
<img src="https://imgur.com/qprHdol.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/bn7uryS.png" height="80%" width="80%">
<br />  
<p align="center">
<img src="https://imgur.com/ivU2eS6.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/jZNQb4w.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/F8JtMGl.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/F2t80im.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/F2t80im.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/NWAUmja.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/EpKLGEG.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/Vfkthzp.png" height="80%" width="80%">
<br />







  
  4. Install and confgure WordPress: Download and install the WordPress CMS on the EC2 instances. Configure the database connection settings to connect to the RDS instance.

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
