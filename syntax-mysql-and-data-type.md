# Convention:

PART1: 

- Uppercase: SQL Command

- Lowercase: human wrote

- Brackets: group

PART2:

- etc... means the previous statement can be multi

- \* and followed by a number means they are a family(interchangeable)

# Data Type:

 ```mysql 
 VARCHAR(225) 
 ```
 
```mysql
CHAR(exact_length)
```

```mysql
INT
```

```mysql
DECIMAL(65,30)
```

```mysql
FLOAT(7)
```
```mysql
DOUBLE(m,d)
```

```mysql
DATE, TIME, DATETIME, TIMESTAMP
```

```mysql
YEAR(4)
```

# Day and Time functions:

```mysql
DATEDIFF(date,date)
```

```mysql
DATE_ADD(DATE, INTEREVAL, expr unit) = date +/- INTERVAL expr unit
```

```mysql
CURDATE()
```

```mysql
CURTIME()
```

```mysql
NOW(), CURRENT_TIMESTAMP
```

```mysql
DATE_FORMAT(DOCS)
```

```mysql
DAYNAME(column_name), MONTHNAME(column_name)
```

```mysql
cast(value AS data_type)
```

# Logical operators:

```mysql
Not Equal(!=)
```

```mysql
NOT LIKE
```

```mysql
Greater than(>)
```

```mysql
Less than(<)
```

```mysql
Greater Than Or Equal To(>=)
```

```mysql
Less Than Or Equal To(<=)
```

```mysql
AND = &&
```

```mysql
OR = ||
```

```mysql
NOT BETWEEN/ BETWEEN where_value AND
```

```mysql
NOT IN/ IN(desired_value, etc...)
```

# CASE_STATEMENT:

- IF(true_statement, print_value, else_value)
  
  ```mysql
  CASE
     WHEN column_name IS NULL THEN "print_value"
     WHEN column_name [=] when_value THEN "print_value" etc...
     ELSE "print_value"
  END AS column_name
```
  
- Numeric Functions:
 
- ROUND(value, round_number)

**Notice:**

sFunction_value = column_name, text_string, string_function, COUNT(*)

- vd: SELECT CONCAT("hello", " ", "world") AS "Example"; 
 
- vd: SELECT CONCAT(SUBSTRING("hello", -3), " ", "world") AS "Example";
# String Functions:
- CONCAT(sFunction_value, " ", sFunction_value)
- CONCAT_WS("-", sFunction_value, sFunction_value)
- SUBSTRING(sFunction_value, number, number/negative_number)
-SUBSTR(sFunction_value, number, number/negative_number)
-REPLACE(sFunction_value, replace_input, replace_output)
-REVERSE(sFunction_value)
-CHAR_LENGTH(sFunction_value)
-LENGTH(sFunction_value)
-UPPER(sFunction_value)
-LOWER(sFunction_value)
-LEFT(sFunction_value, number_to_extract_tring)
*Notice:
-count_value = *, column_name, string_function
*Aggregate Functions:
-COUNT(DISTINCT count_value, etc...)
-MIN(column_name)
-MAX(column_name)
-SUM(column_name)
-AVG(column_name)



# Syntax:
PART1(11):
-SHOW DATABASES;
-CREATE DATABASE name;
-DROP DATABASE name;
-USE database_name;
-SELECT DATABASE();
-CREATE TABLE table_name
 (
  <column_name data_type DEFAULT value NOT NULL UNIQUE ON UPDATE desired_value>, etc...

   id INT NOT NULL AUTO_INCREMENT PRIMARY KEY*1,
   PRIMARY KEY (column_name, etc...)*2

   foreign_key INT
   FOREIGN KEY(foreign_key) REFERENCES foreign_table(foreign_column)
   ON DELETE CASCADE 
 );
-SHOW TABLES;
-SHOW COLUMNS FROM <table_name>;
-DESC table_name*1;
-DESCRIBE table_name*2;
-DROP TABLE table_name, etc...;
*Notice:
-INSERT an empty value = default value
-Logical operators = [=]
-select_value = *, column_name, DISTINCT count_value, string_function, aggregate_function, IFNULL(column_name,print_value)
-where_value = column_name, desired_data, sub_query
-COUNT(*) = group every row in the entire table or,
count for each mega_rows(data grouped by GROUP BY)
-GROUP BY use with Aggregate Functions
-Backslash(\) used in LIKE means escape character
-Underscore used in LIKE means the number of characters you want to find
-Can ORDER BY number, number is refering to the position after SELECT,
and ORDER BY can have two input, if input number one has the same data,
input number two will sort one more time, based on it
vd: ORDER BY number, etc...
PART2(3):
-INSERT INTO <table_name> (column_name, etc...)
 VALUES (value, etc...), etc...
-SELECT select_value AS alias_name, etc...
 UNION
 CASE_STATEMENT
 FROM table_name 
 WHERE column_name [=] where_value AND column_name LIKE "% desired_data %" || "_"
 GROUP BY column_name, etc...
 HAVING column_name [=] where_value
 ORDER BY column_name, etc... DESC/ASC
 LIMIT number, etc...
;
-SHOW WARNINGS;
PART3(2):
-UPDATE table_name
 SET column_name = new_data
 WHERE column_name <= desired_data || column_name> || <LIKE "% desired_data %" || "_">
;
-DELETE FROM table_name
 WHERE column_name <= desired_data || column_name> || <LIKE "% desired_data %" || "_">
;



# Subquery:
-vd: SELECT * FROM books
     WHERE pages = (SELECT MIN(pages)
                    FROM books);
                    
# ONE TO ONE/Cross join:
-SELECT * FROM table_one, table_two;

# Implicit inner join:

# SELECT * FROM table_one, table_two
 WHERE table_one.column_name = table_two.column_name
 
# ONE TO MANY:
-SELECT * FROM  table_one
 LEFT/RIGHT JOIN table_two
 ON table_one.column_name = table_two.column_name
 
# MANY TO MANY:
-SELECT * FROM  table_one
 LEFT/RIGHT JOIN table_two
 ON table_one.column_name = table_two.column_name

 LEFT/RIGHT JOIN table_two
 ON table_one.column_name = table_two.column_name























































