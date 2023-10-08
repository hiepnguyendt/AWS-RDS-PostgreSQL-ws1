---
title : "Database and Schemas"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.2. </b> "
---
Welcome to PostgreSQL! If this is your first time looking at **PostgreSQL**, we encourage you to check out the official [About PostgreSQL](https://www.postgresql.org/about/)  webpage.

In this module, we are going to explore **Databases and Schemas.**

{{% notice info %}}
This chapter assumes you have setup and configured pgAdmin. If you haven't, please complete the pgAdmin module before proceeding.
{{% /notice %}}

#### Explore Databases

 1.In your pgAdmin tool, click the *>* in front of **rdspg-fcj-labs** to expand it.

 ![rdspg-fcj-labs](/images/2/2-2/1.png)
 {{% notice note %}}
 You see 3 breakouts: Databases, Login/Group Roles, and Tablespaces.\
 In this section, we will focus on **Databases**. And we'll cover **Login/Group** Roles in a later section.
 {{% /notice %}}

 
 2.Expand the Databases node.

 ![Databases](/images/2/2-2/2.png)

 From a terminology standpoint, the PostgreSQL instance `(rdspg-fcj-labs)` you have created is known as a PostgreSQL **cluster**. A cluster contains one or more **databases**. While the users/roles of a cluster are shared across a cluster, no data is shared across databases. In other words, when a customer connects to a cluster, that connection is required to specify the database it wants to work with and that connection can only work within a single database at a time.\
 {{% notice note %}}
 you see a handful of databases within the `pglab` cluster.
 {{% /notice %}}


 {{%expand "What is the `rdsadmin` database ?" %}}The database named rdsadmin is a database that is reserved for use by the RDS/Aurora control plane.{{% /expand%}}

 3.Right-click on the **Databases** node and choose **Create**, then click **Databases**

 ![Create Databases](/images/2/2-2/3.png)

 4.Name the database `first_database` (but don't save it yet)

 ![My Databases](/images/2/2-2/4.png)

 {{% notice note %}}
 The database has an owner. This role can control and assign permissions for this database to other roles. The owner defaults to the role you are currently logged in with pgAdmin. Also note that you can alter the owner of most PostgreSQL objects even after they are originally created.
 {{% /notice %}} 

 5.Now click on the **Definition** tab

 ![Definition](/images/2/2-2/5.png)

 {{% notice note %}}
 There are [various settings](https://www.postgresql.org/docs/11/sql-createdatabase.html)  that can be changed. You don't need to change anything for now.
 {{% /notice %}}

 6.Click on the **SQL** tab

 ![SQL](/images/2/2-2/6.png)
 The SQL tab shows you a preview of the generated SQL command that pgAdmin is going to run.

 7.Click **Save** \
 8.Find your new database in the navigator and expand it.
 ![SQL](/images/2/2-2/7.png)

#### Explore Schemas
A database contains one or more named **schemas**, which in turn contain tables and other objects like views and functions. The objects in a given PostgreSQL schema can be owned by different users and the schema name has no implied correlation to the name of the schema owner.

As described in the [PostgreSQL Documentation](https://www.postgresql.org/docs/11/ddl-schemas.html)


> " The same object name can be used in different schemas without conflict; for example, both `schema1` and `myschema` may contain tables named mytable. Unlike databases, schemas are not rigidly separated: a user may access objects in any of the schemas in the database he is connected to, if he has privileges to do so.
>
> There are several reasons why one might want to use schemas:
>
> - To allow many users to use one database without interfering with each other.
> - To organize database objects into logical groups to make them more manageable.
> - Third-party applications can be put into separate schemas so they cannot collide with the names of other objects.
>
> Schemas are analogous to directories at the operating system level, except that schemas cannot be nested."

1.Expand the **Schemas** node and see a default **public schema**.

![Schema](/images/2/2-2/8.png)



2.Right-click on the **Schemas** node and choose **Create**, then click **Schema**.

![create schema](/images/2/2-2/9.png)

3.Name the schema `first_schema`

![named schema](/images/2/2-2/10.png)

{{% notice note %}}
 The schemas have an owner and also have security permissions and default privileges for new objects created in the schema (you can click on the Security tab and the Default Permissions tab in the Create Schema dialog if you want).
 {{% /notice %}}


4.Click **Save** to create the new schema.

{{% notice info %}}
PostgreSQL **schemas** can be different from how other databases like Oracle implement schemas. In Oracle, schemas are directly mapped 1:1 to users. In PostgreSQL, schemas are not coupled directly to a specific user(role).
{{% /notice %}}

As discussed in the [documentation](https://www.postgresql.org/docs/11/ddl-schemas.html#DDL-SCHEMAS-PORTABILITY) ,


> "In the SQL standard, the notion of objects in the same schema being owned by different users does not exist. Moreover, some implementations do not allow you to create schemas that have a different name than their owner. In fact, the concepts of schema and user are nearly equivalent in a database system that implements only the basic schema support specified in the standard. Therefore, many users consider qualified names to really consist of username.tablename. This is how PostgreSQL will effectively behave if you create a per-user schema for every user. Also, there is no concept of a public schema in the SQL standard. For maximum conformance to the standard, you should not use (perhaps even remove) the public schema."

**A note about the** `search_path`
Referencing objects via Qualified names, such as `first_schema.first_table`, is tedious to write, and hard-coding a particular schema name into an application is not ideal. The solution is to use unqualified names, such as `first_table` and this is made possible via the PostgreSQL `search_path`.

As discussed in the [documentation](https://www.postgresql.org/docs/11/ddl-schemas.html#DDL-SCHEMAS-PATH) ,

> "The system determines which table is meant by following a search_path, which is a list of schemas to look in. The first matching table in the search path is taken to be the one wanted. If there is no match in the search path, an error is reported, even if matching table names exist in other schemas in the database.
>
> The first schema named in the search path is called the current schema. Aside from being the first schema searched, it is also the schema in which new tables will be created if the CREATE TABLE command does not specify a schema name."

By default, the search_path is set to $user,public. As the documentation states
> "The first element specifies that a schema with the same name as the current user is to be searched. If no such schema exists, the entry is ignored. The second element refers to the public schema that we have seen already."

{{% notice info %}}
It should be noted that PostgreSQL does not have the concept of synonyms like certain other databases. You can use the search_path to handle some, but not all, of the capabilities that synonyms offer. For an example of implementing other synonym-like functionality in PostgreSQL, see this [blog post](https://www.dbbest.com/blog/convert-oracle-synonyms-to-postgresql/) .
{{% /notice %}}

**Congratulations!**

You have learned the basics about PostgreSQL Databases and Schemas.---
title : "Database and Schemas"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.2. </b> "
---
Welcome to PostgreSQL! If this is your first time looking at **PostgreSQL**, we encourage you to check out the official [About PostgreSQL](https://www.postgresql.org/about/)  webpage.

In this module, we are going to explore **Databases and Schemas.**

{{% notice info %}}
This chapter assumes you have setup and configured pgAdmin. If you haven't, please complete the pgAdmin module before proceeding.
{{% /notice %}}

#### Explore Databases

 1.In your pgAdmin tool, click the *>* in front of **rdspg-fcj-labs** to expand it.

 ![rdspg-fcj-labs](/images/2/2-2/1.png)
 {{% notice note %}}
 You see 3 breakouts: Databases, Login/Group Roles, and Tablespaces.\
 In this section, we will focus on **Databases**. And we'll cover **Login/Group** Roles in a later section.
 {{% /notice %}}

 
 2.Expand the Databases node.

 ![Databases](/images/2/2-2/2.png)

 From a terminology standpoint, the PostgreSQL instance `(rdspg-fcj-labs)` you have created is known as a PostgreSQL **cluster**. A cluster contains one or more **databases**. While the users/roles of a cluster are shared across a cluster, no data is shared across databases. In other words, when a customer connects to a cluster, that connection is required to specify the database it wants to work with and that connection can only work within a single database at a time.\
 {{% notice note %}}
 you see a handful of databases within the `pglab` cluster.
 {{% /notice %}}


 {{%expand "What is the `rdsadmin` database ?" %}}The database named rdsadmin is a database that is reserved for use by the RDS/Aurora control plane.{{% /expand%}}

 3.Right-click on the **Databases** node and choose **Create**, then click **Databases**

 ![Create Databases](/images/2/2-2/3.png)

 4.Name the database `first_database` (but don't save it yet)

 ![My Databases](/images/2/2-2/4.png)

 {{% notice note %}}
 The database has an owner. This role can control and assign permissions for this database to other roles. The owner defaults to the role you are currently logged in with pgAdmin. Also note that you can alter the owner of most PostgreSQL objects even after they are originally created.
 {{% /notice %}} 

 5.Now click on the **Definition** tab

 ![Definition](/images/2/2-2/5.png)

 {{% notice note %}}
 There are [various settings](https://www.postgresql.org/docs/11/sql-createdatabase.html)  that can be changed. You don't need to change anything for now.
 {{% /notice %}}

 6.Click on the **SQL** tab

 ![SQL](/images/2/2-2/6.png)
 The SQL tab shows you a preview of the generated SQL command that pgAdmin is going to run.

 7.Click **Save** \
 8.Find your new database in the navigator and expand it.
 ![SQL](/images/2/2-2/7.png)

#### Explore Schemas
A database contains one or more named **schemas**, which in turn contain tables and other objects like views and functions. The objects in a given PostgreSQL schema can be owned by different users and the schema name has no implied correlation to the name of the schema owner.

As described in the [PostgreSQL Documentation](https://www.postgresql.org/docs/11/ddl-schemas.html)


> " The same object name can be used in different schemas without conflict; for example, both `schema1` and `myschema` may contain tables named mytable. Unlike databases, schemas are not rigidly separated: a user may access objects in any of the schemas in the database he is connected to, if he has privileges to do so.
>
> There are several reasons why one might want to use schemas:
>
> - To allow many users to use one database without interfering with each other.
> - To organize database objects into logical groups to make them more manageable.
> - Third-party applications can be put into separate schemas so they cannot collide with the names of other objects.
>
> Schemas are analogous to directories at the operating system level, except that schemas cannot be nested."

1.Expand the **Schemas** node and see a default **public schema**.

![Schema](/images/2/2-2/8.png)



2.Right-click on the **Schemas** node and choose **Create**, then click **Schema**.

![create schema](/images/2/2-2/9.png)

3.Name the schema `first_schema`

![named schema](/images/2/2-2/10.png)

{{% notice note %}}
 The schemas have an owner and also have security permissions and default privileges for new objects created in the schema (you can click on the Security tab and the Default Permissions tab in the Create Schema dialog if you want).
 {{% /notice %}}


4.Click **Save** to create the new schema.

{{% notice info %}}
PostgreSQL **schemas** can be different from how other databases like Oracle implement schemas. In Oracle, schemas are directly mapped 1:1 to users. In PostgreSQL, schemas are not coupled directly to a specific user(role).
{{% /notice %}}

As discussed in the [documentation](https://www.postgresql.org/docs/11/ddl-schemas.html#DDL-SCHEMAS-PORTABILITY) ,


> "In the SQL standard, the notion of objects in the same schema being owned by different users does not exist. Moreover, some implementations do not allow you to create schemas that have a different name than their owner. In fact, the concepts of schema and user are nearly equivalent in a database system that implements only the basic schema support specified in the standard. Therefore, many users consider qualified names to really consist of username.tablename. This is how PostgreSQL will effectively behave if you create a per-user schema for every user. Also, there is no concept of a public schema in the SQL standard. For maximum conformance to the standard, you should not use (perhaps even remove) the public schema."

**A note about the** `search_path`
Referencing objects via Qualified names, such as `first_schema.first_table`, is tedious to write, and hard-coding a particular schema name into an application is not ideal. The solution is to use unqualified names, such as `first_table` and this is made possible via the PostgreSQL `search_path`.

As discussed in the [documentation](https://www.postgresql.org/docs/11/ddl-schemas.html#DDL-SCHEMAS-PATH) ,

> "The system determines which table is meant by following a search_path, which is a list of schemas to look in. The first matching table in the search path is taken to be the one wanted. If there is no match in the search path, an error is reported, even if matching table names exist in other schemas in the database.
>
> The first schema named in the search path is called the current schema. Aside from being the first schema searched, it is also the schema in which new tables will be created if the CREATE TABLE command does not specify a schema name."

By default, the search_path is set to $user,public. As the documentation states
> "The first element specifies that a schema with the same name as the current user is to be searched. If no such schema exists, the entry is ignored. The second element refers to the public schema that we have seen already."

{{% notice info %}}
It should be noted that PostgreSQL does not have the concept of synonyms like certain other databases. You can use the search_path to handle some, but not all, of the capabilities that synonyms offer. For an example of implementing other synonym-like functionality in PostgreSQL, see this [blog post](https://www.dbbest.com/blog/convert-oracle-synonyms-to-postgresql/) .
{{% /notice %}}

**Congratulations!**

You have learned the basics about PostgreSQL Databases and Schemas.