---
title : "Create RDS PostgreSQL DB"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 2.7. </b> "
---


#### To create an RDS PostgreSQL DB, follow these steps:

1. Open the **Amazon RDS** [console](https://console.aws.amazon.com/rds/).

![Create EC2 SG](/images/preparation/db/1.png)

2. Click **Create database**.
3. For **Database engine**, select **PostgreSQL**.
4. For **Version**, select the version of PostgreSQL that you want to use.

![Create EC2 SG](/images/preparation/db/2.png)

5. For **Template**, select a template for your DB instance. A template is a pre-configured configuration for a DB instance.

![Create EC2 SG](/images/preparation/db/3.png)

6. For **Availability** and **Durability**, For DB instance identifier, enter a name for your DB instance.

![Create EC2 SG](/images/preparation/db/4.png)

7. For **DB instance identifier**, enter a unique name for your database instance.
8. For **Master username**, enter the username for the master user of your database instance.
9. For **Master password**, enter a strong password for the master user of your database instance.

![Create EC2 SG](/images/preparation/db/5.png)

10. For **DB instance class**, select the instance class that you want to use for your database instance. The instance class will determine the amount of CPU and memory that is allocated to your database instance.

![Create EC2 SG](/images/preparation/db/6.png)

11. For **Storage**, select the amount of storage that you want to allocate for your database instance.

![Create EC2 SG](/images/preparation/db/7.png)

12. For **Connectivity**, select option **Connect to a EC2 compute resource**, then choose your **App server** instance which you have created in the earier step.

![Create EC2 SG](/images/preparation/db/8.png)

13. For **DB subnet group**, select the DB subnet group that you want to use for your DB instance.
14. For **VPC security groups**, select the security groups that you want to use for your DB instance.

![Create EC2 SG](/images/preparation/db/9.png)

15. Expand **Additional configuration**, Enter **5432** for **database port**

![Create EC2 SG](/images/preparation/db/10.png)

16. For **Database authentication**, choose option that you want to use

![Create EC2 SG](/images/preparation/db/11.png)

17. For **Monitoring**, select the monitoring options that you want to use for your database instance

![Create EC2 SG](/images/preparation/db/12.png)

18. Expand **Additional configuration**:
- For **Database option**, fill name for database you want create after lauch RDS PostgreSQL 
- For **DB parameter group**, leave everything with default setting

![Create EC2 SG](/images/preparation/db/13.png)

19. For **Backup**, select the backup options that you want to use for your database instance.

![Create EC2 SG](/images/preparation/db/14.png)

20. Click **Create database**.

Your database instance will be created and will be displayed in the list of database instances. You can connect to it using a PostgreSQL client, such as psql, pgAdmin4. To do this, you will need the hostname, port number, and username and password for your database instance.

**Here are some additional things to keep in mind when creating an RDS PostgreSQL DB:**
{{%expand "Click here" %}}
- You can only create an RDS PostgreSQL DB in a VPC that is in the same AWS Region as the database engine that you plan to use.
- You must choose an instance class that is compatible with the PostgreSQL version that you want to use.
- You can choose to create your database instance in a single Availability Zone (AZ) or in multiple AZs. If you choose to create your database instance in multiple AZs, you will be able to take advantage of high availability and disaster recovery features.
- You can choose to enable encryption for your database instance. This will encrypt your data at rest and in transit.
- You can choose to enable backups for your database instance. This will allow you to restore your database to a previous point in time if something goes wrong.
{{% /expand%}}


