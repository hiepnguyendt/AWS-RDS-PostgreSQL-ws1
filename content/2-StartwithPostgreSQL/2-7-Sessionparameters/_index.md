---
title : "Session parameters"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 2.7. </b> "
---

 {{% notice note%}}
 This chapter assumes you have completed the Basic DML chapter. If you haven't, please complete the Basic DML module before proceeding.
 {{% /notice %}}

 This chapter will talk about [PostgreSQL Parameters](https://www.postgresql.org/docs/11/runtime-config.html) . Specifically, it will focus on parameters that can be changed at the session-level. For system-wide parameters, you would leverage RDS/Aurora's Parameter Group mechanism.

 1.In pgAdmin, click on the rdspg-fcj-labs node, then click on **Dashboard**, then click on **Configuration**.

 ![parametter](/images/2/2-7/49.png)

 This shows you the current setting of all the **PostgreSQL parameter settings**.

 2.In the search box, type **``search``**

 ![parametter](/images/2/2-7/50.png)

 This filters down the list of parameter settings.

 3.Click on **first_database**, then choose **Query Tool** icon. Then paste and run the following SQL:

 ```SELECT * FROM pg_settings where context = 'user';```

 ![parametter](/images/2/2-7/51.png)

 This shows you the parameter sessions that can be changed for a session, as well as their current setting.

 4.Paste and run the following SQL:

 ```show search_path```
 ![parametter](/images/2/2-7/52.png)
 The ``SHOW`` command is another way to view the current value of a setting for your session.

 5.Paste and run the following SQL:
 ```show all```
  ![parametter](/images/2/2-7/53.png)
 This shows you yet another way to view the current value of all of the parameter settings for your session.

 6.Paste and try the following SQL:
 ```select * from first_table;```
 ![parametter](/images/2/2-7/54.png)
  This fails because PostgreSQL is not able to find a table named **first_table** in the schemas in the current **search_path**.\
 7.Paste and try the following SQL:
 ```SET search_path TO first_schema, public;   ```
 ![parametter](/images/2/2-7/55.png)

 8.Paste and try the following SQL again:
  ```select * from first_table;```
  ![parametter](/images/2/2-7/56.png)
 This now works because we updated the **search_path** parameter setting for our session.

 {{% notice tip%}}
 When making changes to system parameters via RDS/Aurora Parameter Groups, it is a good idea to confirm that your parameter change has been applied by using one of the techniques above, such as "SHOW ALL", to confirm that the expected parameter value is in effect. Sometimes people can be confused because their Parameter Group change can be made but the actual parameter setting change does not happen [until the next reboot](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Troubleshooting.html#CHAP_Troubleshooting.Parameters). Confirming the value using "SHOW ALL" or one of the other methods can save you confusion and time
 {{% /notice %}}