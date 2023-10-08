---
title : "Using pgAdmin4 to connect to RDS PostgreSQL"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 4.1. </b> "
---


 {{% notice note%}}
 In this section, we will use **pgAdmin4** to connect to a RDS for PostgreSQL DB instance, so we need create DB as public.\
 You can use the open-source tool **pgAdmin4** to connect to your RDS for PostgreSQL DB instance. You can download and install pgAdmin from http://www.pgadmin.org/ without having a local instance of PostgreSQL on your client computer
 {{% /notice %}}


 1.Launch the **pgAdmin4** application on your client computer.\
 2.On the **Dashboard** tab, choose **Add New Server.**

 ![connecting](/images/4/4-1/14.png)
 3.In the **Create - Server** dialog box, type a name on the **General** tab to identify the server in pgAdmin4. 
 
 ![connecting](/images/4/4-1/1.png)
 
 4.In the **Connection** tab, type the following information from your DB instance:
 - For **Host**, The Endpoint of the RDS PostgreSQL DB, for example mypostgresql.c6c8dntfzzhgv0.us-east-2.rds.amazonaws.com.
 - For **Port**, type the assigned port.
 - For **Username**, type the user name that you entered when you created the DB instance. 
 - For **Password**, type the password that you entered when you created the DB instance.

 ![connecting](/images/4/4-1/2.png)
 
 5. In the **SSH Tunnel** tab, enable the SSH tunnel feature and enter the following information
 - For **Host**: The hostname or IP address of the bastion host.
 - For **Port**: The SSH port number.
 - For **Username**: The username that you use to SSH into the bastion host.
 - For **Identity file**: choose the keypair that you have selected when create ec2 bastion host. 

  ![connecting](/images/4/4-1/3.png)
  
 5.Choose **Save**.
 The server has been added to the pgAdmin4 and its dashboard is visible on the screen:
 ![connecting](/images/4/4-1/6.png)

 {{% notice tip%}}
 If you have any problems connecting, see [Troubleshooting connections to your RDS for PostgreSQL instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ConnectToPostgreSQLInstance.html#USER_ConnectToPostgreSQLInstance.Troubleshooting).
 {{% /notice %}}