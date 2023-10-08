---
title : "Create DB Subnet group"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 2.4. </b> "
---


#### To create a DB subnet group on AWS, follow these steps:

1. Open the Amazon RDS [console](https://console.aws.amazon.com/rds/)
2. In the navigation pane, choose **Subnet groups** and click on **Create DB Subnet Group**.

![Create EC2 SG](/images/preparation/4/1.png)

3. For **Name** and **Description**, type in a name and description for your DB subnet group.
4. For **VPC**, select the VPC in which you want to create your DB subnet group.

![Create EC2 SG](/images/preparation/4/2.png)

5. Select the subnets that you want to include in your DB subnet group. Make sure to select subnets in at least two different Availability Zones (AZs).
6. Click **Create**.

![Create EC2 SG](/images/preparation/4/3.png)

Your DB subnet group will be created and will be displayed in the list of DB subnet groups.

**Here are some additional things to keep in mind when creating a DB subnet group:**
- You can only create a DB subnet group in a VPC that is in the same AWS Region as the database engine that you plan to use.
- You must include at least one subnet in each AZ in which you want to deploy your DB instance.
- You cannot modify a DB subnet group once it has been created. If you need to change the subnets in your DB subnet group, you must create a new one.
- You can use a DB subnet group to create a DB instance in any AZ in the VPC. 