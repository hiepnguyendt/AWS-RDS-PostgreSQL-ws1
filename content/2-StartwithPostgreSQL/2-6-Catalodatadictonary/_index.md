---
title : "Catalog and Data dictionary"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 2.6. </b> "
---

 {{% notice note%}}
 This chapter assumes you have completed the Basic DML chapter. If you haven't, please complete the Basic DML module before proceeding.
 {{% /notice %}}
 This chapter introduces the PostgreSQL [Data Dictionary](https://www.postgresql.org/docs/11/ddl-schemas.html#DDL-SCHEMAS-CATALOG).

 #### The pg_catalog schema

 In addition to public and user-created schemas, each database contains a pg_catalog schema, which contains the system tables and all the built-in data types, functions, and operators.

 These are a set of tables used to store dynamic and static metadata for the PostgreSQL database and can be thought of as the “data dictionary” for the database. These tables are used for internal “bookkeeping”-type activities. All System catalog tables start with the pg_*prefix and can be found in the [pg_catalog schema](https://www.postgresql.org/docs/11/catalogs-overview.html)

 1.In pgAdmin, expand the **rdspg-fcj-labs** node, then expand the **Databases** node, then expand the **first_database** node, then expand the **Catalogs** node, then expand the **PostgreSQL Catalog**, then expand **Tables**. 

 ![catalog](/images/2/2-6/43.png)

 You can see the tables in the [pg_catalog schema](https://www.postgresql.org/docs/11/catalogs-overview.html).

 2.Click on the **first_database**, then choose **Query Tool** icon

 3.Paste and run this command to see an example of querying the **pg_catalog** directly: 

 ```select * from pg_tables where schemaname='pg_catalog';```
 ![catalog](/images/2/2-6/44.png)

#### The Statistics Collector Views (also part of pg_catalog)

 The Statistics Collector is a special subsystem which collects runtime dynamic information about the current activities in the database instance. For example, [statistics collector views](https://www.postgresql.org/docs/11/monitoring-stats.html#MONITORING-STATS-DYNAMIC-VIEWS-TABLE)  are useful to determine how frequently a particular table is accessed and if the table is scanned or accessed using an index.

 1.Paste and run this command to see an example of one of the **Statistics Collector** views:

 ```SELECT * FROM pg_stat_activity WHERE STATE = 'active';```

 ![catalog](/images/2/2-6/45.png)

2.lick on the **rds-pg-labs** node. Then click on **Dashboard**. Then click on **Sessions** in the Server activity section.
 ![catalog](/images/2/2-6/46.png)

 Here, pgAdmin is showing you the same **pg_stat_activity** information for your PostgreSQL cluster.

 Tip: Performance Insights  is a great way to visualize current and historical activity and wait events. We encourage you to start with Performance Insights for performance-related diagnostics.

 {{% notice tip%}}
 [Performance Insights](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PerfInsights.html)  is a great way to visualize current and historical activity and wait events. We encourage you to start with Performance Insights for performance-related diagnostics.
 {{% /notice %}}

 3.Paste and run this command to see an example of one of the **Statistics Collector** views:
 ```select * from information_schema.tables;```

 ![catalog](/images/2/2-6/48.png)