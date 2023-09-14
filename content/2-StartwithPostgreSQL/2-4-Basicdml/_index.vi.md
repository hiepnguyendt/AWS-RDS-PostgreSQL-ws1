---
title : "Basic DML"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 2.4. </b> "
---

 This chapter will talk about queries and basic DML.
 
 {{% notice note%}}
 This chapter assumes you have completed the **Tables and Datatypes** chapter. If you haven't, please complete the Tables and Datatypes module before proceeding.
 {{% /notice %}}

#### Insert data into our first table
 1.In your pgAdmin tool, right click on `first_table` under your `first_schema` inside your `first_database`. Choose Scripts, then SELECT Script

 ![insert data](/images/2/2-4/insert_data.png)

 This will create a boilerplate insert statement for our table that we can edit.

 ![insert data](/images/2/2-4/insert_data_1.png)

 2.Highlight the ? placeholder and replace it with `'my first row'`. Don't forget to use the `'` single-quote mark to surround your text.

 ![insert data](/images/2/2-4/insert_data_2.png)

 3.Click on the Play icon to execute this command.

 This will run your command and insert your first row.

 ![insert data](/images/2/2-4/insert_data_2.png)

 {{%expand "What does 'INSERT 0 1' mean ?" %}}The 1 in INSERT 0 1 means that it inserted 1 row. The 0 is only applicable if the table uses the classic PostgreSQL OID (Object Identifier), and if so, the 0 represents the actual OID created. Otherwise, it will always return the value 0. These days you probably will not create tables using OIDs, but if you are curious you can read more about OIDs in the documentation .{{% /expand%}}

 {{%expand "Is my row committed ?" %}}
 By default, pgAdmin is set with AutoCommit on, so, yes, this new row should be committed. You can see/change the AutoCommit mode by clicking on the icon next to the Play icon in the pgAdmin Query Editor:
 ![insert data](/images/2/2-4/insert_data_3.png)
 {{% /expand%}}

#### Query our first table

 1.In your pgAdmin tool, right click on `first_table` under your `first_schema` inside your `first_database`. Choose Scripts, then SELECT Script

 ![select](/images/2/2-4/select.png)

 2.Click on the Play icon to execute this command.

  ![select](/images/2/2-4/select_1.png)

 This will run your command and you should see your first row.

 ![select](/images/2/2-4/select_2.png)


#### Create table second table if not exists
 1.Using one of the open query editors, paste in the following create command and then click the Play icon to execute it:
 ``` 
 create table if not exists first_schema.second_table(
    col_pk serial,
    col_money numeric(12,2),
    col_short_str varchar(100),
    col_datetime timestamp(0) without time zone
  );
 ```
 ![add table](/images/2/2-4/add_table.png)

#### Insert into our second table
 1.Using one of the open query editors, paste in the following insert command and then click the Play icon to execute it:

 ```
 INSERT INTO first_schema.second_table(
  col_money, col_short_str, col_datetime)
  VALUES (40.25, 'short string', TIMESTAMP '2004-10-19 10:23:54') 
 returning col_pk;
 ```
  ![insert data to table](/images/2/2-4/insert_data_to_table2.png)

 Notice that because we specified `returning col_pk`, we see the auto-generated unique value of col_pk in the Data Output section. Remember that when we created second_table that we specified that col_pk used the `SERIAL` datatype (which is like the AUTO_INCREMENT datatype in other database engines).

#### Experimenting with Datatype conversions
 1.In one of the open query editors, paste the following select command and click the Play icon to execute it:
 ```
 SELECT '40.25' col1, 40.25 col2;
 ```
 ![datatype](/images/2/2-4/datatype.png)

 Notice in the Data Output section that `col1` is a text datatype while `col2` is a numeric datatype.

 {{% notice note%}}
 Unlike certain other databases (specifically Oracle), you do not need to have a FROM clause in your SELECT statement. So if you are in the habit of writing `SELECT 'something' FROM dual`; in Oracle, you can leave the `FROM dual` off in PostgreSQL. There is no `dual` table in PostgreSQL.
 {{% /notice %}}

 2.Now run this query:

 ```
 SELECT '40.25' col1, 40.25 col2, '40.25'::numeric col3, numeric '40.25' col4, cast('40.25' as numeric) col5;
 ```
 ![datatype](/images/2/2-4/datatype_1.png)

 Notice in the Data Output section that `col3`, `col4`, and `col5` are all examples of text datatypes that have been converted to numeric datatypes. These 3 columns demonstrate 3 ways that you can do datatype conversion in PostgreSQL SQL statements.