---
title : "Using EC2 instance to connect to RDS PostgreSQL"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 4.2 </b> "
---

#### To connect to an RDS PostgreSQL DB using an EC2 instance, follow these steps:

1. Connect to EC2 instance (App server) via MobaXterm.
2. Download and install updates linux OS.
 You can use the following command to download and install: 
 ```
 cat /etc/os-release 
 cat /etc/system-release
 sudo yum update -y

 ``` 
 ![connecting](/images/4/4-2/1.png)
 
 3. Add PostgreSQL Amazon extras repository

 PostgreSQL is part of the amazon extras library.\
 To check the available postgresql version in the Amazon extras repository:
 ``` 
 amazon-linux-extras | grep postgresql
 ```
 ![connecting](/images/4/4-2/3.png)

 To enable the Amazon extras repository:

 ``` 
 sudo amazon-linux-extras enable postgresql14
 ```

 4. Install the psql client:

 ``` sudo amazon-linux-extras install postgresql14 ```

 5. To install the pgbench:

 ``` sudo yum install postgresql-contrib ```

 6. Recheck verions **psql** & **pgbench**
```
psql --version
pgbench --version
```


  ![connecting](/images/4/4-2/5.png)

7. Connect to the remote RDS PostgreSQL:

```psql -h rdspg-fcj-labs.cssuddr073hp.us-east-1.rds.amazonaws.com -U masteruser -d pglab```

- -h: RDS PostgreSQL endpoint
- -U: username for the master user of your database instance
- -d: name for database 



