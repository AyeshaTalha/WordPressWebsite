<h1>AWS WordPress Website</h1>

<h2>Description</h2>
This project involves deploying and hosting a WordPress website on the Amazon Web Services (AWS) platform. WordPress is a popular content management system (CMS) used for creating and managing websites. By leveraging AWS services, the project aims to provide a scalable, secure, and highly available infrastructure for the WordPress website<br />


<h2> Key Components and Technologies </h2>

1. Amazon EC2: Amazon Elastic Compute Cloud (EC2) is used to provision virtual servers, known as EC2 instances, to host the WordPress application. EC2 instances provide the necessary compute resources to run the website.

2. Amazon RDS: Amazon Relational Database Service (RDS) is used to set up and manage a MySQL or Aurora database for storing the website's content, settings, and user data. RDS provides a scalable and managed database solution.

3. Amazon VPC: With Amazon Virtual Private Cloud (Amazon VPC), you can launch AWS resources in a logically isolated virtual network that you've defined. This virtual network closely resembles a traditional network that you'd operate in your own data center, with the benefits of using the scalable infrastructure of AWS.

4. Subnets: A subnet is a range of IP addresses in your VPC. You can create AWS resources, such as EC2 instances, in specific subnets.

5. Application Load Balancer: Elastic Load Balancing automatically distributes your incoming traffic across multiple targets, such as EC2 instances, containers, and IP addresses, in one or more Availability Zones. It monitors the health of its registered targets, and routes traffic only to the healthy targets. Elastic Load Balancing scales your load balancer as your incoming traffic changes over time. It can automatically scale to the vast majority of workloads. 

<h2>Project Workflow </h2>
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

10. Now, lets add the Security Groups for EC2 instances, Application Load Balancer, RDS Database and EFS File System. From the VPC main console, Scroll down on the lefthand side to the Security Groups option. Click on Create Security Group.
<p align="center">
<img src="https://imgur.com/zJtGuNl.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/M3qyDXZ.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/02eyGtH.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/dchucwR.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/JMneJsd.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/RXRCaN1.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/RXRCaN1.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/rKqCdyT.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/FppW81h.png" height="80%" width="80%">
<br />

11. Navigate back to RDS Console. On the lefthand side select the Subnet Groups option. Click on Add Subnet Group and select the subnets. 
<p align="center">
<img src="https://imgur.com/IinnFAH.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/AEGHjKZ.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/PmXIlPX.png" height="80%" width="80%">
<br />

12. On the RDS Console, Click on Databases. Click on Create Database. Enter the following details and click on Create Database. Remember the Credentials you enter. We are going to be use these to login later.
<p align="center">
<img src="https://imgur.com/QuQ7dql.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/PmXIlPX.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/VwPeMRs.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/e4mBu2d.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/jZDZsbn.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/yg7elyB.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/wTx72rS.png" height="80%" width="80%">
<br />

13. The next step is to create an EFS File system.
<p align="center">
<img src="https://imgur.com/0cJIA1W.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/DdP3Rcz.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/n0JseaN.png" height="80%" width="80%">
<br />

14. Now, lets create the security group for SSH. After creating it, edit the inbound rules for Web Server Security Group and EFS Security Group to add an SSH rule for the SSH Security Group as destination.  
<p align="center">
<img src="https://imgur.com/qCK6vx5.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/STnXQYL.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/RMICiOn.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/2lmyB7K.png" height="80%" width="80%">
<br />

15. The next step is to launch a setup server with appropriate security groups. On the AWS Console, Navigate to EC2. On the EC2 Dashboard, Click on Running instances and the Click on Create Instance. Enter the details and click on Create Instance. After creating the Instance, copy the Public IPV4 address of the server. We will use it to SSH into the server using PUTTY.
<p align="center">
<img src="https://imgur.com/DO94Sfl.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/kjlZciJ.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/FTFBHkS.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/4EfWfhv.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/qxZDHT7.png" height="80%" width="80%">
<br />

16. Next, we have to SSH into the Server. For this we will use PUTTY and SSH into the Server through the IP address we copied.
<p align="center">
<img src="https://imgur.com/3c2OG1o.png" height="80%" width="80%">
<br />


17. The next step is to install WordPress and move the files to EFS. The code for this is given above in the code.txt file. When you edit config file, make sure you edit the database name, database user and password.
<p align="center">
<img src="https://imgur.com/LWOmRQR.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/AiWpTk8.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/Jvtj8p9.png" height="80%" width="80%">
<br />
 <p align="center">
<img src="https://imgur.com/aloFdng.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/ABJEpm6.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/GUKGmtC.png" height="80%" width="80%">
<br />

17. Create an Application Load Balancer in the VPC we created. Use Private Subnet 1. The user data for the ALB is given above in the userdata.txt file. Copy and paste it in the user data section. Make sure you change the NFS mount. Copy the DNS name and paste it in the Web Browser. You will get the WordPress website Hello World!
<p align="center">
<img src="https://imgur.com/E3HHKmx.png" height="80%" width="80%">
<br />
 
  
<h2>Benefits of AWS WordPress Website </h2>

- Scalability: AWS allows you to scale the infrastructure resources, such as EC2 instances and RDS databases, based on website traffic and demand, ensuring optimal performance.
- High availability: By leveraging multiple availability zones and load balancing, AWS provides high availability for the WordPress website, minimizing downtime and ensuring continuous access.
- Security: AWS offers various security features, such as IAM for access control, ACM for SSL/TLS certificates, and VPC for network isolation, to enhance the security of the WordPress website.
- Cost-effectiveness: AWS provides a pay-as-you-go pricing model, allowing you to optimize costs by scaling resources as needed and only paying for the actual usage.
<h2>Project Workflow:</h2>
