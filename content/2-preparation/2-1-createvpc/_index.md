---
title : "Create a VPC"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1. </b> "
---
 
1. Go to the [VPC console](https://console.aws.amazon.com/vpc/) and click **Create VPC**.

![Create a VPC](/images/preparation/1/1.png)

2. For **Resources to create**, choose **VPC and more**.
3. Enter a name for your VPC and select a **CIDR block**. The CIDR block is the range of IP addresses that will be available to your VPC. Make sure to choose a CIDR block that is large enough for your needs, but not so large that you waste IP addresses.

![Create a VPC](/images/preparation/1/2.png)

4. Select values for **Number of public subnets**, **Number of private subnets** and **NAT Gateway**.

![Create a VPC](/images/preparation/1/3.png)
5. Review your VPC resources, then click **Create VPC**

![Create a VPC](/images/preparation/1/4.png)