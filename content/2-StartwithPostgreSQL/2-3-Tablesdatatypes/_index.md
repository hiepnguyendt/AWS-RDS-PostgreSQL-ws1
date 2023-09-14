---
title : "Tables and Datatypes"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 2.3. </b> "
---

In this module, we are going to explore Tables and Datatypes.


{{% notice note %}}
This chapter assumes you have completed the Databases and Schemas chapter. If you haven't, please complete the Databases and Schemas module before proceeding.
{{% /notice %}}

**What is a Table and why do I see PostgreSQL sometimes call them Relations ?**\
From the **PostgreSQL documentation** ,

> "PostgreSQL is a relational database management system (RDBMS). That means it is a system for managing data stored in relations. Relation is essentially a mathematical term for table. The notion of storing data in tables is so commonplace today that it might seem inherently obvious, but there are a number of other ways of organizing databases. Files and directories on Unix-like operating systems form an example of a hierarchical database. A more modern development is the object-oriented database.
>
> Each table is a named collection of rows. Each row of a given table has the same set of named columns, and each column is of a specific data type. Whereas columns have a fixed order in each row, it is important to remember that SQL does not guarantee the order of the rows within the table in any way (although they can be explicitly sorted for display).
>
> Tables are grouped into databases, and a collection of databases managed by a single PostgreSQL server instance constitutes a database cluster."
 
 #### Explore Tables

 1.In your pgAdmin tool, expand your **first_schema** inside your **first_database**.

 ![table](/images/2/2-3/11.png)

 {{% notice note %}}
 The different kinds of objects (tables, views, functions, etc) that can be part of a PostgreSQL schema.
 {{% /notice %}}


 2.Right-click on **Tables** and choose **Create** then select **Table**

 ![create table](/images/2/2-3/12.png)

 3.Name your table **`first_table`**.

  ![named table](/images/2/2-3/13.png)


 {{% notice note %}}
 There is an option to make your table partitioned. For this **first_table**, we will not use table partitioning.
 {{% /notice %}}

 {{% notice info %}}
 Table Partitioning in PostgreSQL is an interesting subject. It is interesting because table partitioning has evolved across the PostgreSQL versions. In earlier versions (version 9 and earlier), table partitioning was indirectly supported via the PostgreSQL table inheritance feature (see below). Starting with PostgreSQL version 10, table partition became a native declarative feature. A key thing to remember is that the exact set of table partitioning features supported are tied to the PostgreSQL version. So, be sure you refer to the [table partitioning documentation](https://www.postgresql.org/docs/11/ddl-partitioning.html)  tied to the version of PostgreSQL you are using.
 {{% /notice %}}

 4.Click on Columns to advance to the Columns tab. Then click on the **+** sign. Then enter `col1` for the Name. Fill out `text` for the Data type. Click Yes for Not NULL. Click Yes for Primary Key.

 ![ẹnded table](/images/2/2-3/14.png)


  {{% notice note %}}
 There is an option to inherit columns from other tables. We will not use table inheritance for this first_table, but it is an interesting and useful PostgreSQL capability to be aware of.
 {{% /notice %}}
 {{% notice info %}}
 Table Inheritance in PostgreSQL can be a useful tool for database designers. Table inheritance lets a child table inherit all of the columns of its parent table(s). Further, you can write queries against parent tables that reference the rows of the parent table and all of its descendent tables, too. See the example in the [table inheritance documentation](https://www.postgresql.org/docs/11/ddl-inherit.html)  to better understand the capabilities.
 {{% /notice %}}

 5.Browse the available options on the other tabs and end up on the SQL tab. Then click Save.

  ![saved table](/images/2/2-3/15.png)


 **Congratulations!**

 You have learned the basics about PostgreSQL Tables and Datatypes.