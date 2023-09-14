---
title : "Querying Data"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 4.2. </b> "
---

After using pgAdmin4 to conntect to RDS PostgreSQL. Now We can perform the basic query statements in this chapter:
- Create table ``fcj_users`` in the **pglab** database
- Insert data into the table ``fcj_users``
- View all the recording in the table
- View full name user and nationality
- Get all user from Swedish or American and date of birth from 1980 to 1990. Sort output list descending by date_of_birth
- List top 5 the youngest users 
- List top 5 the oldest users
- Check whether the user is missing a date of birth, or first name or last name



Right-click on the name of the database to open the menu and click on the **“Query Tool”** button from the list:

![querying data](/images/4/4-2/1.png)

1.Create table ``fcj_users`` in the **pglab** database

Type the following query in the query tool to create a new table:

```
CREATE TABLE fcj_user(
    user_id SERIAL NOT NULL PRIMARY KEY,
    first_name VARCHAR(100),
    last_name VARCHAR(100),
    gender char(1),
    date_of_birth DATE,
    nationality VARCHAR (20)
)
```
![querying data](/images/4/4-2/2.png)

2.Insert data into the table **fcj_users**

Insert the data into the **fcj_users** table using the following query:
 ```
 INSERT INTO fcj_users (first_name,last_name,gender,date_of_birth,nationality) VALUES
 ('Malin','Akerman','F','1978-05-12','Swedish'),
('Tim','Allen','M','1953-06-13','American'),
('Julie','Andrews','F','1935-10-01','American'),
('Ivana','Baquero','F','1994-06-11','Bristish'),
('Lorraine','Bracco','F','1954-10-02','Mexican'),
('Alice','Braga','F','1983-04-15','Japanese')
('Marlon','Brando','M','1924-04-03','American')
('Adrien','Brody','M','1973-04-14','Mexican'),
('Peter','Carlberg','M','1950-12-08','Chinese'),
('Gemma','Chan','F','1982-11-29','Japanese'),
('Chen','Chang','M','1976-10-14','Mexican'),
('Graham','Chapman','M','1941-01-08','Japanese'),
('Pei-pei','Cheng','F','1946-12-04','Mexican'),
('Maggie ','Cheung','F','1964-09-20','American'),
('Min-sik','Choi','M','1962-05-30','Chinese'),
('Yun-fat','Chow','M','1955-05-18','American'),
('John','Cleese','M','1939-10-27','British'),
('Paddy','Considine','M','1973-09-05','Mexican'),
('Abbie','Cornish','F','1982-08-07','Swedish'),
('Brian','Cox','M','1946-06-01','Swedish'),
('Scatman','Crothers','M','1910-05-23','American'),
('Russell','Crowe','M','1964-04-07','American'),
('Tom','Cruise','M','1962-07-03','Swedish'),
('Darlan','Cunha','M','1988-07-26','American'),
('Willem','Dafoe','M','1955-07-22','British'),
('Paul','Dano','M','1984-06-19','Swedish'),
('Daniel','Day-Lewis','M','1957-04-29','Swedish'),
('Robert','De Niro','M','1943-08-17','British'),
('Marion','Brando','M','1924-04-03','American'),
(null,'Denden','M','1950-01-23','Mexican'),
('Leonardo','DiCaprio','M','1974-11-11','American'),
('Peter','Dinklage','M','1969-06-11','British'),
('Hiroki','Doi','M','1999-08-10','Japanese'),
('Kirsten','Dunst','F','1982-04-30','Swedish'),
('Shelley','Duvall','F','1949-07-07','British'),
('Ralph','Fiennes','M','1962-12-22','British'),
('Leandro','Firmino','M','1978-06-23','Swedish'),
('Carrie','Fisher','F','1956-10-21','American'),
('Harrison','Ford','M','1942-07-13','American'),
('Darian','Cunha','M','1988-07-26','American'),
('Jodie','Foster','F','1962-11-19','Chinese');
 ```
![querying data](/images/4/4-2/4.png)

3.View all the recording in the table

Type the following query in the query tool to view all recording:
`SElECT * FROM fcj_users;`

4.View full name user and nationality

Type the following query in the query tool :
```
SELECT first_name || ' ' || last_name || ' from ' || nationality AS "Full name" & nationality FROM fcj_users;
```

![querying data](/images/4/4-2/5.png)


5.Get all user from Swedish or American and date of birth from 1980 to 1990. Sort output list descending by date_of_birth

Type the following query in the query tool :

```
SELECT * FROM fcj_users
WHERE nationality = 'Swedish' OR
      nationality = 'American' AND
      date_of_birth BETWEEN '1980-01-01' AND '1990-12-31'
ORDER BY date_of_birth DESC;
```

![querying data](/images/4/4-2/6.png)

6.List top 5 the youngest users

Type the following query in the query tool :

```
SELECT * FROM fcj_users
ORDER BY date_of_birth DESC
FETCH FIRST 5 ROW ONLY;
```

![querying data](/images/4/4-2/7.png)

7.List top 5 the oldest users


Type the following query in the query tool :
```
SELECT * FROM fcj_users
ORDER BY date_of_birth ASC
FETCH FIRST 5 ROW ONLY;
```
![querying data](/images/4/4-2/8.png)

9.Check whether the user is missing a date of birth, or first name or last name
 
 ```
 SELECT *
 FROM fcj_users
 WHERE date_of_birth IS NULL
 OR first_name IS NULL
 OR last_name IS NULL ;
 ```
 ![querying data](/images/4/4-2/9.png)