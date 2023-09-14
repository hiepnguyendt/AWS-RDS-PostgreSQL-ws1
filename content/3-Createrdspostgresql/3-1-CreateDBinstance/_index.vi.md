---
title : "Create DB instane"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 3.1. </b> "
---


 1.Open [AWS Management console](https://aws.amazon.com/premiumsupport/knowledge-center/sign-in-console/),
 - Find **RDS** 
 - Select **RDS** 

 ![create_db](/images/3/3-1/1.1.png)

 2.Click **Create database** to start the configuration process.
 ![create_db](/images/3/3-1/2.1.png)

 In the **Choose a database** creation method section, ensure the **Standard Create** option is selected. 
 ![create_db](/images/3/3-1/3.1.png)
 Next, in the **Engine options** section, choose the **PostgreSQL** engine type and the PostgreSQL 15.3-R2 version.
 ![create_db](/images/3/3-1/4.png)

 In the **Templates** section, select **Free tier**.

 ![create_db](/images/3/3-1/5.png)

 {{% notice note%}}
 When using RDS free  tier which has not support feature Availability and Durability.
 {{% /notice %}}

 In the **Settings** section, set the DB instance identifier to rdspg-fcj-labs. Configure the name and password of the master database user, with the most elevated permissions in the database.

 ![create_db](/images/3/3-1/6.png)

 In the **DB instance size** section, select B**urstable classes**, and choose db.t3.micro in the size drop-down

  ![create_db](/images/3/3-1/7.png)

 In the **Storage** Section, leave with default setting.\ 
 Expand **Storage autoscaling**, then **Uncheck **the Enable storage autoscaling box.
 ![create_db](/images/3/3-1/8.png)

 In the **Connectivity** section, leave with default setting
 In the **Database authentication** section, choose **Password authentication**

 ![create_db](/images/3/3-1/9.png)
 
  In the **Monitoring** section, we will use default setting
 ![create_db](/images/3/3-1/10.png)

 In the **Additional configuration**,
 - Fill your **Initial database name**
 - Uncheck **Enable automated backups**
 - Uncheck **Enable encryption**
 ![create_db](/images/3/3-1/11.1.png)

 - Check all option in **Log exports**
 - Check **Enable auto minor version upgrade**
 - Choose **No preference** for **Maintenance window**

 ![create_db](/images/3/3-1/12.png)

Finally, review **Estimated Monthly costs** then select **Create database**
 ![create_db](/images/3/3-1/13.png)