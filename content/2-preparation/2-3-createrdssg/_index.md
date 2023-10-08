---
title : "Create RDS Security Group"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 2.3. </b> "
---


#### To create an EC2 security group in the AWS console:

1. Go to the [EC2 console](https://us-east-1.console.aws.amazon.com/ec2/home?region=us-east-1#Home:).
2. In the navigation pane, choose **Security Groups**.
3. Choose Create Security Group.

![Create EC2 SG](/images/preparation/2/1.png)

4. For **VPC**, choose the VPC where you want to create the security group.
5. For **Security group name**, enter a descriptive name for the security group.
6. For **Description**, enter a description for the security group.

![Create EC2 SG](/images/preparation/3/1.png)

7. Modify Inbound Rule

![Create EC2 SG](/images/preparation/3/2.png)

8. Modify Outbound Rule

![Create EC2 SG](/images/preparation/3/3.png)

9. Click **Create**.

![Create EC2 SG](/images/preparation/3/4.png)

Once you have created the security group for RDS PostgreSQL