## MYSQL QUERIES

# 1. Introduction to Database
## 1.1 Terminologies used
See below a list of terminologies used in MYSQL.
```
1. Database
A database is a structured collection of data stored in a computer system. In MySQL, a database is a container for storing tables, views, triggers, procedures, and other database objects.

2. Table
A table is the fundamental storage structure in MySQL. It's organized in rows and columns, where each row represents a record and each column represents a field. Tables store data in a structured format.

3. Row
A row is a single, horizontal record in a table. Each row contains data for all the columns of the table. Rows are also referred to as records.

4. Column
A column defines a vertical field in a table. It represents the attribute of the data (like name, age, or email). Each column has a specific data type, such as INT, VARCHAR, DATE, etc.

5. Primary Key
A primary key is a unique identifier for each record in a table. It ensures that no two rows have the same value in the primary key column(s). The primary key field cannot be null.

6. Foreign Key
A foreign key is a field (or a set of fields) in one table that uniquely identifies a row of another table. It creates a relationship between two tables and enforces referential integrity.

7. Index
An index is a data structure used to speed up queries. By creating an index on one or more columns of a table, MySQL can retrieve rows more efficiently. However, indexes may slow down insert and update operations.

8. Query
A query is a request for data or information from a database. In MySQL, queries are written in SQL (Structured Query Language) to retrieve, insert, update, or delete data.

9. SQL (Structured Query Language)
SQL is the standard language used to communicate with relational databases like MySQL. It consists of statements like SELECT, INSERT, UPDATE, and DELETE.

10. Normalization
Normalization is the process of organizing data to minimize redundancy and improve data integrity. It involves splitting large tables into smaller ones and defining relationships between them.

11. Join
A join is a SQL operation that combines data from two or more tables based on a related column between them. Types of joins include INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN.

12. View
A view is a virtual table in MySQL, created by a query. It does not store data but allows you to see the result of a SELECT query as a table. Views can simplify complex queries and enhance security by restricting access to certain data.

13. Stored Procedure
A stored procedure is a reusable block of SQL code that can be executed repeatedly. It helps in automating repetitive tasks and allows you to perform complex operations in MySQL.

14. Trigger
A trigger is a special kind of stored procedure that automatically executes when certain events occur in a database, like inserting or deleting a row.

15. Transaction
A transaction is a sequence of SQL operations that are executed as a single unit. It ensures that either all changes made in the transaction are saved (commit) or none are saved (rollback).

16. Commit
A commit is the SQL command used to save all the changes made during a transaction to the database. Once committed, the changes cannot be undone.

17. Rollback
A rollback is the SQL command used to undo the changes made during a transaction, reverting the database to its previous state before the transaction started.

18. Schema
A schema is the overall structure of a database, including tables, views, indexes, procedures, and relationships. It represents the design and organization of data.

19. Data Types
Data types define the kind of data a column can hold. Common data types in MySQL include:

- INT: Integer numbers.
- VARCHAR: Variable-length strings.
- DATE: Date values.
- DECIMAL: Fixed-point numbers for financial calculations.
- TEXT: Large text fields.
20. Cursor
A cursor is a database object used to retrieve data one row at a time. It's often used within stored procedures or functions when dealing with complex data retrieval scenarios.

21. Constraints
Constraints are rules applied to table columns to ensure data integrity. Examples include:

- NOT NULL: Ensures a column cannot have null values.
- UNIQUE: Ensures all values in a column are unique.
- CHECK: Ensures that all values in a column meet a specific condition.
```


# 2. Getting Started with MySQL
## 2.1 Installation in Windows
## 2.2 Installation in Linux machine.

## 2.3 How to access MySQL database
#### 2.3.1 Connecting to the server
The access to a MySQL database depends to the deployment or the location of the database. To keep it simple:- see the following.
To connect to the server, run the command:

```
> mysql -h host -u user -p   
#assumes that the database is hosted on a different server. Host is the IP or hostname of the hosting server.
OR
> mysql -u user -p
#Replace the user with the name of the user who has the database access.

#Other alternatives in Linux. Login automatically using the default username and password.
> sudo mysql --defaults-file=/etc/mysql/debian.cnf

OR
> sudo -i
> mysql

```

#### 2.3.2 To Disconnect from MySQL server
To disconnect from MySQL server, run the following commands
```
> \q         
OR
> QUIT   #then press enter.
```



## 2.4 Getting Started
To get a list of options provided by mysql. MySQL has to be installed for the following command to run.

```
> mysql --help
```

### GENERAL COMMANDS
```
#return version and current date
> SELECT VERSION(), CURRENT_DATE; 
#Returns current date and time
> SELECT NOW();

#Use MySQL as calculator
> SELECT 10*4;
#Select current logged user
> SELECT USER()
```


##### NOTES:
```
1. Statements in MySQL are not case sensitive. - Use any font as preferred.
```


# 3. Creating and Managing Databases

## 3.1 Creating Databases
- Get a list of database available
```
SHOW DATABASES;
```
- Switch to the named database.
```
USE databaseone;
```
- Create a database and swith to it.
```
CREATE DATABASE db-name;
USE db-name;
```

## 3.2 CREATE A DATABASE USER
To interact with a database, you need a user. This could be a different user other than the default. A default user is created on MySQL installation. Its highly recommended to create a different user with specific privileges other than using the root user who has the right to manage all databases.

```
CREATE USER 'myuser'@'localhost' IDENTIFIED BY 'mypassword';
```
Explanation: Replace myuser and mypassword with your preffered details.
- localhost means that the user can only access the database from the same machine. To allow remote access, use the following:
```
CREATE USER 'myuser'@'%' IDENTIFIED BY 'mypassword';
```

## 3.2.1 Granting Privileges to a user
After creating a user, you need to assign them privileges to interact with the database. There are different privileges that a user can be granted. 


Below is a list of specific privileges that can be granted to MySQL users:
1. **ALL PRIVILEGES** : This gives the user full permissions to perform all actions on the specified database
2. **SELECT** :  Allows users to select (read) data from tables.
3. **INSERT** : Allows users to insert data into tables.
4. **UPDATE** :  Allows users to update existing data in tables.
5. **DELETE** : Allows users to delete data from tables.
6. **CREATE** : Allows users to create new databases or tables
7. **DROP** : Allows users to delete databases or tables.
8. ***INDEX** : Allows users to create and remove indexes on tables.
9. **ALTER** : Allows users to modify the structure of existing tables (e.g., adding/removing columns).
10. **CREATE VIEW** : Allows users to create views (virtual tables based on queries).
11. **SHOW VIEW** : Allows users to view the definition of views.
12. **EXECUTE** : Allows users to execute stored procedures and functions.
13. **LOCK TABLES** : Allows users to lock tables for the duration of their session.
14. **RELOAD** : Allows users to reload or refresh database resources (e.g., flush caches).
15. **SUPER** : Grants the user superuser privileges (admin-level, can override certain restrictions).
16. **FILE** : Allows users to read and write files on the server.


```
GRANT ALL PRIVILEGES ON mydatabase.* TO 'myuser'@'localhost'; 
```

- Give this user privilages on the database created
- The .* part refers to all the tables within that database.

- To give a user access to a specific table, do this:

```
GRANT ALL PRIVILEGES ON mydatabase.table-name TO 'myuser'@'localhost'; 
```
- TO 'myuser'@'localhost': This applies the privileges to the specified user on the localhost.


- Grant a specific privilege
```
GRANT SELECT ON mydatabase.* TO 'myuser'@'localhost';
```
- Grant multiple specific privileges
```
GRANT SELECT, INSERT, UPDATE ON mydatabase.* TO 'myuser'@'localhost';
```
- Grant privileges on all databases and tables
```
GRANT SUPER ON *.* TO 'myuser'@'localhost';
FLUSH PRIVILEGES;   #save the changes.
```
- The Flush command forces MySQL to reload these settings immediately. Without this command, changes might not apply until you restart the MySQL service.


## 3.2.2 Revoking Privileges
If you need to remove a privilege, you can use the REVOKE command.

- removes the INSERT and UPDATE privileges from the user while leaving any other granted privileges intact.
```
REVOKE INSERT, UPDATE ON mydatabase.* FROM 'myuser'@'localhost';
```
- To revoke all privileges from a MySQL user
```
REVOKE ALL PRIVILEGES, GRANT OPTION ON *.* FROM 'myuser'@'localhost';
```
- The above removes all privileges the user has and the ability for the user to grant privileges to others.




## 3.3 Understanding Data Types
### MySQL Data Types
This section provides a quick reference to commonly used MySQL data types. Each data type is described briefly to help you understand when and how to use it.

## Numeric Data Types

- **INT**: A standard integer data type. Can store whole numbers between -2,147,483,648 and 2,147,483,647.
- **TINYINT**: A very small integer. Can store whole numbers between -128 and 127.
- **SMALLINT**: A small integer. Can store whole numbers between -32,768 and 32,767.
- **MEDIUMINT**: A medium-sized integer. Can store whole numbers between -8,388,608 and 8,388,607.
- **BIGINT**: A large integer. Can store whole numbers between -9,223,372,036,854,775,808 and 9,223,372,036,854,775,807.
- **FLOAT**: A floating-point number. Used to store approximate numeric values with fractional components.
- **DOUBLE**: A double-precision floating-point number. Offers more precision than `FLOAT`.
- **DECIMAL**: A fixed-point number. Used for precise numeric values, such as currency. You can specify the number of digits and the number of digits after the decimal point.

## String Data Types

- **CHAR**: A fixed-length string. Used for storing text strings of a specific length. The length is specified in parentheses.
- **VARCHAR**: A variable-length string. Used for storing text strings of varying lengths. The maximum length is specified in parentheses.
- **TEXT**: A large variable-length string. Used for storing long text data. The maximum length is 65,535 characters.
- **MEDIUMTEXT**: A medium-sized text field. Can store up to 16,777,215 characters.
- **LONGTEXT**: A large text field. Can store up to 4,294,967,295 characters.

## Date and Time Data Types

- **DATE**: A date value in the format `YYYY-MM-DD`.
- **DATETIME**: A date and time value in the format `YYYY-MM-DD HH:MM:SS`.
- **TIMESTAMP**: A timestamp value in the format `YYYY-MM-DD HH:MM:SS`. Automatically updates to the current date and time when a record is modified.
- **TIME**: A time value in the format `HH:MM:SS`.
- **YEAR**: A year value in the format `YYYY`.


## Enumeration Data Types

- **ENUM**: An enumeration. Used for storing a predefined set of values. You specify the allowed values in the definition (e.g., `'small', 'medium', 'large'`).
- **SET**: A set. Similar to `ENUM`, but allows multiple values to be selected from the predefined set.

## Boolean Data Type

- **BOOLEAN**: A data type representing a boolean value. Internally stored as `TINYINT(1)`. `TRUE` is represented as `1`, and `FALSE` as `0`.


## Notes

- Use appropriate data types based on the size, precision, and nature of the data you intend to store.
- Be mindful of performance implications when choosing between different types, especially with large datasets.
- Wrong Data types used result in issues:
    - **Wasted Storage Space**
    - **Reduced Query Performance**
    - **Inefficient Indexing**
    - **Increased Memory Usage**
    - **Poor Cache Efficiency**
    - **Higher Network and Backup Costs**


## 3.3 Creating Tables

```
#List all tables.
SHOW TABLES;
```
Note: To list/create/query tables, you need to have selected the desired database to work with. 
use this command to switch to your desired database.
```
#Get a list of all available databases
SHOW DATABASE;

#Select your desired database for use.
USE <database-name>;

#Create a database
CREATE DATABASE <database-name>;
```

## CREATING A TABLE
```
#Note the table name - pet and the data types used in the field names.

CREATE TABLE pet (name VARCHAR(20), owner VARCHAR(20),
species VARCHAR(20), sex CHAR(1), birth DATE, death DATE);

#Inspect table to display the structure of a table;
DESCRIBE <table-name>;
OR
DESC <table-name>;

```

## 3.4 Inserting Data into Tables

The data can be inserted or loaded from a txt file.
### How to insert data
```
#Insert as one record
INSERT INTO pet
VALUES ('Puffball','Diane','hamster','f','1999-03-30',NULL);

#Insert multiple records

INSERT INTO pet (name, owner, species, sex, birth, death) VALUES
('Fluffy', 'John', 'Dog', 'M', '2018-06-15', NULL),
('Bella', 'Sarah', 'Cat', 'F', '2016-09-21', NULL),
('Max', 'David', 'Dog', 'M', '2017-04-11', NULL),
('Charlie', 'Emily', 'Parrot', 'M', '2020-11-02', NULL),
('Luna', 'Anna', 'Rabbit', 'F', '2019-07-19', '2023-03-05'),
('Daisy', 'Michael', 'Dog', 'F', '2015-03-22', NULL),
('Milo', 'James', 'Cat', 'M', '2021-01-13', NULL),
('Coco', 'Rachel', 'Bird', 'F', '2018-08-28', NULL),
('Rocky', 'Lucas', 'Hamster', 'M', '2019-05-25', NULL),
('Lucy', 'Olivia', 'Dog', 'F', '2020-10-14', NULL);

```
### How to LOAD Data from a .txt
- **Some settings have to be updated as this may cause errors.**

- **Populate your data in a .txt file and load using the following command**

```
#have the file under the path /var/lib/mysql-files/
LOAD DATA LOCAL INFILE '/var/lib/mysql-files/pet.txt' INTO TABLE pet;
```

```
If you get the error below, proceed and do the necessary settings
''LOAD DATA LOCAL INFILE './pet.txt' INTO TABLE pet;
ERROR 3948 (42000): Loading local data is disabled; this must be enabled on both the client and server sides
in mysql''

```
#### How to resolve the above error
```
1. Step 1
#In LINUX
- Open the MySQL configuration file (/etc/mysql/my.cnf or /etc/my.cnf) in a text editor
> sudo nano /etc/mysql/my.cnf
- Add the following line under the [mysqld] section:
> local_infile=1
and if the section [mysql] does not exist, add it and add the line given. 
ie:
[mysql]
local_infile=1
secure_file_priv=''
- Then Restart
> sudo systemctl restart mysql

#Windows
- Open the MySQL configuration file (my.ini), typically located in C:\ProgramData\MySQL\MySQL Server X.X\my.ini.
- Add the same line under the [mysqld] section:
local_infile=1

2. Step 2
Enable on the MySQL Client
- When connecting to MySQL, add the --local-infile option to enable LOAD DATA LOCAL INFILE for the client.
> mysql --local-infile -u username -p
- If Using a MySQL Client (e.g., MySQL Workbench):
**Check the client settings and enable the local_infile flag.**
- You can verify if local_infile is enabled using the following query:
> SHOW VARIABLES LIKE 'local_infile';
The value should be ON.
```



## 3.5 Primary Keys and Indexes
- **Primary Keys**: is a unique identifier for each record in a database table. It ensures that each row in the table can be uniquely identified, and it enforces two important constraints:
1. Uniqueness: No two rows in the table can have the same primary key value.
2. Non-nullability: The primary key column cannot have NULL values.

Note: The primary key is often chosen from data fields that are naturally unique (such as an ID or Social Security Number), but you can also create artificial primary keys, such as an auto-incrementing integer.

Example:
```
CREATE TABLE pet (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    species VARCHAR(30),
    birth DATE
);
```
In this example, the id column is defined as the primary key, which is unique and automatically increments with each new record.

- **Indexes**: is a data structure that improves the speed of data retrieval. It allows the database to quickly locate rows in a table without scanning every row.

Key Characteristics:
- Indexes are created on columns to speed up queries, especially in large datasets. Small database may not have a positive/notable effect
- An index can be created on one or more columns.
- While indexes speed up retrieval, they can slow down INSERT, UPDATE, and DELETE operations because the index also needs to be updated when data is modified.

Types of Indexes:
- Single-Column Index: An index created on a single column.
```
CREATE INDEX idx_species ON pet (species);
```
- Composite Index: An index created on multiple columns. It is used when queries involve multiple columns.
```
CREATE INDEX idx_name_species ON pet (name, species);
```
- Unique Index: Ensures that all values in the indexed column(s) are unique.
```
CREATE UNIQUE INDEX idx_owner ON pet (owner);
```
- Fulltext Index: Used to speed up searches on text-based data.
```
CREATE FULLTEXT INDEX idx_description ON articles (description);
```
Automatically Created Indexes:
- MySQL automatically creates an index on the primary key column, so there's no need to manually create one for it.
- It also creates indexes for columns that have unique or foreign key constraints.

Using Indexes in Queries: 

When you query a table with an indexed column, MySQL can quickly locate the rows that satisfy the condition.
```
SELECT * FROM pet WHERE species = 'Dog';
```
### 3.5.1 View and manage Index
We can view indexes that have been created already:
Usage:
```
SHOW INDEX FROM table_name;
```
Example:
```
SHOW INDEX FROM pet;
```
We can also delete the index:
Usage:
```
DROP INDEX index_name ON table_name;
```
Example:
```
DROP INDEX idx_species ON pet;
```
# 4. Retrieving Data from a table.
To retrieve data, we use a command. This command can just be a simple command without any condition. To fetch specific data, conditions are added.

## 4.1 Retrieve data without conditions
Usage:
```
SELECT <what_to_select> FROM <which_table>
```


Example: Select all fields from the pet table
```
SELECT * FROM pet;
```
Select and Limit the output
```
SELECT * FROM pet LIMIT 5;
```
Select specific Columns
```
SELECT name, species FROM PET;
```
## 4.2 Retrieve data with conditions
Usage:
```
SELECT what_to_select
FROM which_table
<conditions_to_satisfy>;
```
## 4.2.1 Using WHERE Clause
In this case, identify the unique column that will be used and combine it with any of these these operators =, <=, >=

```
> SELECT * FROM pet WHERE name = 'Luna';


#Get pets on 1998-1-1 and later.
> SELECT * FROM pet WHERE birth >= '1998-1-1';

```

## 4.2.2 Logical Operators (AND, OR, NOT)
AND :: Returns data that meets both conditions.
OR :: Returns data that meets any or both of the conditions specified
```
#Combine conditions using AND Operator.
> SELECT * FROM pet WHERE species = 'dog' AND sex = 'f';
#Combine conditions using OR Operator.
> SELECT * FROM pet WHERE species = 'snake' OR species = 'bird';

#Combined operator AND and OR operators
> SELECT * FROM pet WHERE (species = 'cat' AND sex = 'm')
OR (species = 'dog' AND sex = 'f');

#Use NOT
> SELECT * FROM owner not WHERE owner="James";
#selects all apart from those whose owner is James. 
```
## 4.3 Sorting Results with ORDER BY
Some common ordering methods we can consider:
- **Ascending Order (Smallest to Largest)** : This will sort the data from the smallest to the largest values (default if no ASC or DESC is specified).

```
SELECT name, birth FROM pet ORDER BY birth;

OR

SELECT name, birth FROM pet ORDER BY birth ASC;
```
- **Descending Order (Largest to Smallest)** : This will sort the data from the largest to the smallest values

```
SELECT name, birth FROM pet ORDER BY birth DESC;
```

- **Multiple Columns Sorting** : You can order by multiple columns. The query will first order by the first column, and if there are ties, it will order by the second column.
```
SELECT name, species, birth FROM pet
ORDER BY species, birth DESC;
```
- **Ordering by Expressions** : You can use expressions or functions in the ORDER BY clause.
```
SELECT * FROM pet ORDER BY LENGTH(name);
```
- **Random Order** : To return the data in a random order:
```
SELECT * FROM pet ORDER BY RAND();
```

## 4.4 Limiting Results with LIMIT

## 4.5 Retrieve Distinct data
We may want to select unique entries. eg. Lets select the owners of the pets, ignoring the duplicates if any.
```
SELECT DISTINCT owner FROM pet;
```

## 4.6 Date Calculations
As we retrieve the data, we can calculate how old the pets are in years/months/days. 
```
SELECT name, birth, CURDATE(),
TIMESTAMPDIFF(YEAR,birth,CURDATE()) AS age
FROM pet;
```

We can also extract days or Months or Years from the given dates. 
```
SELECT name, birth, MONTH(birth) FROM pet;
SELECT name, birth, DAY(birth) FROM pet;
SELECT name, birth, YEAR(birth) FROM pet;
```

## 4.7 Working with NULL Values
- NULL value refers to a missing unknown value and is treated differently from known values. Note that NULL values are not 0!

To Filter data based on whether the given column is NULL or otherwiser
```
SELECT * from pet WHERE death IS NOT NULL;
SELECT * from pet WHERE death IS NULL;
```
## 4.8 Pattern Matching
This is used to get data that match a certain criteria. We make use of LIKE and NOT LIKE and not the mathematical operators we have used in the past.

- **Case 1: Filter data based on names beginning with b**
```
SELECT * FROM pet WHERE name LIKE 'b%';
```

- **Case 2: Filter data based on names ending with b**
```
SELECT * FROM pet WHERE name LIKE '%b';
```
- **Case 3: Filter data based on names that have b**
```
SELECT * FROM pet WHERE name LIKE '%b%';
```
- **Case 4: Filter data based on names beginning with ba**
```
SELECT * FROM pet WHERE name LIKE 'ba%';
```
- **Case 5: Filter data based on names that DO NOT begin with ba**
```
SELECT * FROM pet WHERE name NOT LIKE 'ba%';
```
- **Case 6: To find names containing exactly 4 characters, use 4 instances of the _ pattern character:**
```
SELECT * FROM pet WHERE name LIKE '____';
```


## 4.9 Use REGEXP to match patterns
Find names beginning with b, use ^ to match the beginning of the name:
```
SELECT * FROM pet WHERE name REGEXP '^b';
```
Find names ending with a, use $ to match the end of the name
```
SELECT * FROM pet WHERE name REGEXP 'a$';
```
Find names containing a, use this query:
```
SELECT * FROM pet WHERE name REGEXP 'a';
```
Find names containing exactly five characters, use ^ and $ to match the beginning and end of the name,
and five instances of . in between
```
SELECT * FROM pet WHERE name REGEXP '^.....$';
    OR:: using the {n} (“repeat-n-times”) operator
SELECT * FROM pet WHERE name REGEXP '^.{5}$';

```

## 4.9.1 Counting Rows
Get a count of all rows
```
SELECT COUNT(*) FROM pet;
```
Find out how many pets each owner has
```
SELECT owner, COUNT(*) FROM pet GROUP BY owner;
```
Number of animals per species:
```
SELECT species, COUNT(*) FROM pet GROUP BY species;
```
Number of animals per sex:
```
SELECT sex, COUNT(*) FROM pet GROUP BY sex;
```
Number of animals per combination of species and sex
```
SELECT species, sex, COUNT(*) FROM pet GROUP BY species, sex;
```
Filter specific species only
```
SELECT species, sex, COUNT(*) FROM pet
WHERE species = 'dog' OR species = 'cat'
GROUP BY species, sex;
```

## 4.3 Using mysql in Batch Mode
We have alredy seen that to execute SQL commands, we have to first access mysql console. In this section, we will see how to RUN mysql commands from the normal commandline without first accessing the mysql console. 
- **Create a file preferably .sql or .txt file and add the SQL commands eg, commands to retrieve some data.**
- **Proceed to execute the file with the below approach**

```
- create a file named sql-cmmands.sql and add a few commands as below:

USE database-name; #replace with database name where your tables are.
select * from pet where sex="M";

#Add other commands as needed.


#To execute the file/commands:

#Option 1:
> sudo mysql < sql-cmmands.sql

#option 2: Add the required credentials
> mysql -h host -u user -p < sql-commands.sql

#option 3: Add required credentials
> mysql -u user -p < sql-commands.sql

#option 3: In windows, you may get errors: use the following
> mysql -e "source batch-file"

```

# Another use case:: executing a bash of SQL commands
You may be given a list of SQL commands to run and give a report of the out. If the commands in question are many, you need not copy and paste them one by one unless its necessary. 
- Assume you are give a file named pet-commands.sql
- Save it to some location, and from this location access mysql.
- Run the following command to execute the SQL commands from the script. You can also specify the path if you access mysql from any location

```
source pet-commands.sql  

source /path/to/file/pet-commands.sql 
```


# 5. Modifying Data in SQL
In SQL, modifying data is done using INSERT, UPDATE, and DELETE statements. These commands allow you to add, change, or remove data from your database.
1. **INSERT – Adding Data to a Table** : We have already see how we can insert data into our table. Refer to the previous section.
2. **UPDATE – Modifying Existing Data**: The UPDATE statement allows you to change data in existing rows. You specify the table, columns to update, new values, and an optional WHERE clause to limit which rows are updated.

Usage:
```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
Example:
```
UPDATE pet SET owner = 'Alice' WHERE name = 'Fluffy';

```
3. **DELETE – Removing Data from a Table** : The DELETE statement removes rows from a table. You can delete specific rows by using a WHERE condition or delete all rows from a table without a WHERE clause.

Usage:
```
DELETE FROM table_name WHERE condition;
```
Example:
```
DELETE FROM pet
WHERE name = 'Charlie';
```
4. **REPLACE – Insert or Replace Existing Data** :
The REPLACE statement is similar to INSERT, but if a row already exists with the same unique key, it deletes the existing row and inserts the new row.

Usage:
```
REPLACE INTO table_name (columns) VALUES (values);
```
Example:
```
REPLACE INTO pet (name, owner, species, sex, birth, death) VALUES
('Max', 'Sophia', 'Wolf', 'M', '2017-04-11', NULL);
```
5. **TRUNCATE – Deleting All Rows Quickly** :
TRUNCATE removes all rows from a table, but unlike DELETE, it doesn't log individual row deletions, making it faster. It resets any AUTO_INCREMENT counters in the table.
Usage:
```
TRUNCATE TABLE table_name;
```

# 6. SQL JOINS
# 7. Exporting Data from a table
Exporting data from MySQL allows you to save the data from a database table into external files like CSV, SQL dumps, or other formats. This is useful for backups, sharing data, or migrating to other systems.
1. Using SELECT INTO OUTFILE:
SELECT INTO OUTFILE is a built-in SQL command that exports data directly to a file in a specified format. The file is saved on the server where MySQL is running.

Usage:
```
SELECT * INTO OUTFILE '/path/to/file.csv'
FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"'
LINES TERMINATED BY '\n'
FROM table_name;

OR

SELECT * FROM pet INTO OUTFILE '/var/lib/mysql-files/new-backups.csv' 
FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"' 
LINES TERMINATED BY '\n';
```
Note: Due to file permissions, we may not be able to save the file on any directory. By default, use:
/var/lib/mysql-files/
Once the file has been saved, you can now copy/move it to the desired directory. To open it, ensure you give the necessary permissions. eg:
```
chmod 644 file-csv
```

2. Using mysqldump for SQL Dump Export : mysqldump is a command-line utility that exports the structure and/or data of a table or an entire database into a SQL file. This file can be used for backups or to migrate the database.

Usage:
```
mysqldump -u username -p database_name table_name > output_file.sql
```
Example: 
```
mysqldump -u root -p mydatabase pet > pet_table.sql
```
Note: This command is run on the terminal/command prompt console level. Run the command in the location where you want the file to be saved. 

3. Exporting Data as JSON : MySQL 5.7 and later versions support JSON format. You can export data as JSON using SELECT and GROUP_CONCAT to build a JSON-like structure.

- On mysql console
```
SELECT CONCAT(
  '[',
  GROUP_CONCAT(
    JSON_OBJECT('name', name, 'owner', owner, 'species', species)
  ),
  ']'
) AS json_output
FROM pet;
```

- To a file

```
SELECT CONCAT(
  '[',
  GROUP_CONCAT(
    JSON_OBJECT('name', name, 'owner', owner, 'species', species)
  ),
  ']'
) AS json_output
INTO OUTFILE '/var/lib/mysql-files/pet_data.json'
FIELDS TERMINATED BY ''
LINES TERMINATED BY '\n'
FROM pet;
```


4. Using PHPMyAdmin for Exporting Data: PHPMyAdmin offers an easy way to export data through a web interface.
Steps:

- Open PHPMyAdmin and navigate to the database or table you want to export.
- Click on the "Export" tab.
- Choose the format (CSV, SQL, Excel, etc.).
- Click "Go" to download the file.


