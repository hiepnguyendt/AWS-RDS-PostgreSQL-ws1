---
title : "Roles and Users"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 2.5. </b> "
---
 {{% notice note%}}
 This chapter assumes you have completed the Basic DML chapter. If you haven't, please complete the Basic DML module before proceeding.
 {{% /notice %}}

 This chapter will talk about [PostgreSQL Roles](https://www.postgresql.org/docs/11/user-manag.html) . In PostgreSQL, a role encompasses the concept of both users and groups. The CREATE USER and CREATE GROUP statements are actually aliases for the CREATE ROLE statement. The difference is that a user is role with the **LOGIN** privilege.

 Roles are defined at the PostgreSQL cluster level and are valid in all databases within the cluster. Role are not created specific to an individual database.
 
 
 {{% notice info%}}
 In PostgreSQL, schemas are distinct concept from roles/users. This is different than databases such as Oracle.
 {{% /notice %}}
 #### Exploring Existing Roles

 In pgAdmin, expand the **Login/Group Roles** item under your PostgreSQL server.

  ![role](/images/2/2-5/26.png)

  You will see the existing and [default roles](https://www.postgresql.org/docs/11/default-roles.html)  defined in this PostgreSQL cluster. Notice that there are 2 types of icons that pgAdmin uses for roles. If the role has **LOIGN** privileges, then it is drawn as a user (such as rdsadmin and masteruser). Otherwise, it is displayed with a group icon.\


 You can also retrieve this same information by running the following sql query:

 ``` SELECT rolname FROM pg_roles;```

 ![role](/images/2/2-5/27.png)

#### Create a new Role

 1.Right-click on **Login/Group Roles**, then choose **Create**, then choose **Login/Group role**:

  ![role](/images/2/2-5/28.png)

 2.Name the role ``first_role``.
  ![role](/images/2/2-5/28.png)

 3.Browse through the other tabs of the Create role dialog, but don't change anything. End up on the SQL tab. Then click Save.
 ![role](/images/2/2-5/30.png)

 4.Right-click on **first_database** and choose **Query Tool** icon.
 ![role](/images/2/2-5/31.png)
 5.Paste and run the following SQL to grant some [privileges](https://www.postgresql.org/docs/11/ddl-priv.html)  to your new role.

 ```
 GRANT USAGE ON SCHEMA first_schema TO first_role;
 GRANT SELECT ON first_schema.first_table TO first_role;
 ```
 ![role](/images/2/2-5/32.png)

 
 {{% notice note%}}
 we have granted the role both the ability to SELECT from the table, and also the ability to use the schema that contains the table.
 {{% /notice %}}

#### Create a new User

 1.Right-click on **Login/Group Roles**, then choose **Create**, then choose **Login/Group role**:
 ![role](/images/2/2-5/33.png)

 2.Name the role ``first_user``.

 ![role](/images/2/2-5/34.png)

   3.Click on the **Definition** tab. Then enter a Password you will remember.

 ![role](/images/2/2-5/35.png)

 4.Click on the **Privileges** tab. Then set **Can login?** to **Yes**

 ![role](/images/2/2-5/36.png)

 5.Click on the **Membership** tab. Then click in the Roles field and pick ``first_role``

 ![role](/images/2/2-5/37.png)

 6.Finally, click on the **SQL** tab to see what the **SQL** looks like. Then **Save**

 ![role](/images/2/2-5/38.png)

 Now, right-click on the **Servers** node and choose **Create**, then click **Server**


 7.Name the new connection ``first_user_connection``\
 8.Click on the **Connection** tab. Enter the RDS endpoint for the hostname (see notes below if you need help finding it). Enter ``first_user`` for the Username. Enter your **Password** you just defined for the new user. Then click **Save**.
  ![role](/images/2/2-5/39.png)

 9.Expand the **first_user_connection** node, then expand **Databases**. Right-click on **first_database**, then choose **Query Tool** to open up a session as first_user.
   ![role](/images/2/2-5/40.png)

 10.Paste and run this SQL to see if our **first_role** grants work:

 ```select * from first_schema.first_table;```
 ![role](/images/2/2-5/41.png)

 11.Paste and run this SQL to test a table that we have not granted to **first_role**:

 ```select * from first_schema.second_table;```
  ![role](/images/2/2-5/42.png)
 
 {{% notice tip%}}
 Read more about [best practices for PostgreSQL User/Role management](https://aws.amazon.com/blogs/database/managing-postgresql-users-and-roles/)
 {{% /notice %}}



  {{%expand " Want to create additional DBA users (similar to masteruser) for your RDS or Aurora PostgreSQL instance? " %}}
 Try [this script](https://aws.amazon.com/premiumsupport/knowledge-center/rds-aurora-postgresql-clone-master-user/) :
 ```
 --replace thepassword with a real password
 CREATE ROLE new_dba_user WITH PASSWORD 'thepassword' CREATEDB CREATEROLE LOGIN;
 GRANT rds_superuser TO new_dba_user;

 ```
 {{% /expand%}}