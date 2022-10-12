Mysql - SELFDOCS

# Introduction:

**What is Database**

A structured set of computerized data with an accessible interface

**What is MySql**

Mysql is a database management system, a language use to talk to databases

**what makes DBMS(vd: mysql,...) unique**

what makes DBMS unique are the features they offer

# Basic syntax:

**SELECT @@hostname**

```mysql
SELECT @@hostname;
```

**CREATE DATABASE**

```mysql
CREATE DATABASE cat_app;
```

**DROP DATABASE**

```mysql
DROP DATABASE cat_app;
```

**SHOW DATABASES**

```mysql
SHOW DATABASES;
```

**USE DATABASE**

```mysql
USE cat_app;
```

**WHAT IS THE DATABASE WE CURRENTLY IN ?**

```mysql
SELECT database();
```
**SHOW WARNINGS IF THERE ARE WARNINGS**
```mysql
SHOW WARNINGS;
```


# Data types:
- **VARCHAR(225)** 

- **CHAR(exact_length)**

- **INT**

- **DECIMAL(65,30)**

- **FLOAT(7)**

- **DOUBLE(m,d)**

- **DATE, TIME, DATETIME, TIMESTAMP**

- **YEAR(4)**

# Tables in database:

**CREATE TABLE**

```mysql
CREATE TABLE cats
   (
      name VARCHAR(100),
      age  INT
      breedd VARCHAR(100)
   );   
```

**DELETE TABLE**

```mysql
DROP TABLE cats;
```

**HOW DO WE KNOW IT WORKED ?**
```MySql
SHOW TABLES;
```
```mysql
+-------------------+
| Tables_in_cat_app |
+-------------------+
| cats              |
+-------------------+
```

**SHOW INFO ABOUT COLUMNS**

```MySql
SHOW COLUMNS FROM cats;
```
```mysql
+-------+--------------+------+-----+---------+-------+
| Field | Type         | Null | Key | Default | Extra |
+-------+--------------+------+-----+---------+-------+
| name  | varchar(100) | YES  |     | NULL    |       |
| age   | int          | YES  |     | NULL    |       |
+-------+--------------+------+-----+---------+-------+
```

```mysql
DESC cats;
```
```mysql
+-------+--------------+------+-----+---------+-------+
| Field | Type         | Null | Key | Default | Extra |
+-------+--------------+------+-----+---------+-------+
| name  | varchar(100) | YES  |     | NULL    |       |
| age   | int          | YES  |     | NULL    |       |
+-------+--------------+------+-----+---------+-------+
```

**ADDING DATA INTO TABLES**
```mysql
INSERT INTO cats(name, age, breed)
VALUES ("Kitty", 7, "Tabby"), 
       ("Cacao", 3, "Ragdoll");
```

**HOW DO WE REQUIRE NOT NULL(\*) and DEFAULT VALUE(\*)**
```mysql
CREATE TABLE cats2
(
name VARCHAR(100) NOT NULL DEFAULT "unnamed",
age  INT NOT NULL DEFAULT "1",
breed VARCHAR(100) NOT NULL DEFAULT "unvalue"
);
```

**ADDING A UNIQUE IDENTIFIER ON A ROW**
```mysql
CREATE TABLE unique_cats
   (cat_id INT          NOT NULL AUTO_INCREMENT,
    name   VARCHAR(100),
    age    INT,
    breed  VARCHAR(100),
    PRIMARY KEY (cat_id));
```


# BASIC READ
Read all datas in a table

```mysql
SELECT * FROM cats;
```

Read specific fields in a table
```mysql
SELECT name FROM cats;
```

# BASIC WHERE
Look for specific data in a table

```mysql
SELECT * FROM cats WHERE age > 4;
```
# Refining selections

More weapons in the arsenal

**DISTINCT**

return unique data

```mysql
SELECT DISTINCT author_lname FROM books;
```
Output:
```mysql
+----------------+
| author_lname   |
+----------------+
| Lahiri         |
| Gaiman         |
| Eggers         |
+----------------+

```

**ORDER BY**

Sorting result

```mysql
SELECT author_lname FROM books ORDER BY author_lname;
```

Output:
```mysql
+----------------+
| author_lname   |
+----------------+
| Carver         |
| Chabon         |
| DeLillo        |
+----------------+
```

# ALIASES
Aliases in MySQL is used to give a temporary name to a table or a column in a table

```mysql
SELECT cat_id AS id FROM cats;
```

# BASIC UPDATE
```mysql
UPDATE cats 
SET breed = "Shorthair"
WHERE breed = "Tabby";
```
# BASIC DELETE
```mysql
DELETE FROM cats
WHERE age > 4;
```

# String Functions

**CONCAT**
Combine data for cleaner output

```mysql
SELECT 
   author_fname,
   author_lname,
   CONCAT(author_fname, " ", author_lname) AS "Full name"
FROM books;
```
Output:
```mysql
+--------------+----------------+----------------------+
| author_fname | author_lname   | Full name            |
+--------------+----------------+----------------------+
| Jhumpa       | Lahiri         | Jhumpa Lahiri        |
| Neil         | Gaiman         | Neil Gaiman          |
| Dave         | Eggers         | Dave Eggers          |
+--------------+----------------+----------------------+

```


**CONCAT_WS**
Concat with separator

```mysql
SELECT 
   CONCAT_WS(" ", author_fname, author_lname) AS "Full name"
FROM books;
```

**SUBSTRING**
Work with parts of strings

```mysql
SELECT 
   title,
   SUBSTRING(title, 1, 10) AS "Shirt title"
FROM books;
```
Output:

```mysql
+-----------------------------------------------------+-------------+
| title                                               | Shirt title |
+-----------------------------------------------------+-------------+
| The Namesake                                        | The Namesa  |
| Norse Mythology                                     | Norse Myth  |
| American Gods                                       | American G  |
+-----------------------------------------------------+-------------+
```

**REPLACE**
Replace parts of strings

```mysql
SELECT 
   title,
   SUBSTRING(REPLACE(title, "e", 3), 1, 10)
FROM books;
```
Output:

```mysql
+-----------------------------------------------------+------------------------------------------+
| title                                               | SUBSTRING(REPLACE(title, "e", 3), 1, 10) |
+-----------------------------------------------------+------------------------------------------+
| The Namesake                                        | Th3 Nam3sa                               |
| Norse Mythology                                     | Nors3 Myth                               |
| American Gods                                       | Am3rican G                               |
+-----------------------------------------------------+------------------------------------------+
```

**REVERSE**
Super straightforward!

```mysql
SELECT 
   CONCAT(author_fname, " - ", REVERSE(author_fname))
FROM books;
```
Output:

```mysql
+----------------------------------------------------+
| CONCAT(author_fname, " - ", REVERSE(author_fname)) |
+----------------------------------------------------+
| Jhumpa - apmuhJ                                    |
| Neil - lieN                                        |
| Dave - evaD                                        |
+----------------------------------------------------+
```

**CHAR_LENGTH**
Counts characters in string

```mysql
SELECT 
   author_lname,
   CHAR_LENGTH(author_lname) as "length"
FROM books;
```
Output:

```mysql
+----------------+--------+
| author_lname   | length |
+----------------+--------+
| Lahiri         |      6 |
| Gaiman         |      6 |
| Eggers         |      6 |
+----------------+--------+
```
**UPPER and LOWER**
Change a string's case

```mysql
SELECT 
   CONCAT(UPPER(author_lname), " - ", LOWER(author_fname))
FROM books;
```
Output:
```mysql
+---------------------------------------------------------+
| CONCAT(UPPER(author_lname), " - ", LOWER(author_fname)) |
+---------------------------------------------------------+
| LAHIRI - jhumpa                                         |
| GAIMAN - neil                                           |
| EGGERS - dave                                           |
+---------------------------------------------------------+
```
# Relationship basics
**One to one relationship**


# NOTICE:

## Tables in database

- **NULL** is unknown value when a value is not **insert**

- **DEFAULT** is replacement value when the value is not inserted, not when the value is inserted NULL
