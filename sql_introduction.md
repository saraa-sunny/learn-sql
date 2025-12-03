# SQL Introduction ✨

SQL stands for Structured Query Language.  
SQL is a standard language for accessing and manipulating databases.

<br>

## 🎁 What is a database?  

A database is a structured collection of data stored on a computer.It is a powerful tool for storing and organizing data efficiently.  

**📌 Relational databases**   
 A relational database represents a collection of related (two-dimensional) tables. Each of the tables are similar to an Excel spreadsheet, with a fixed number of named columns (the attributes or properties of the table) and any number of rows of data.

Here are two common database types:
* **Relational database management systems (RDBMS)**: This is the most common database type, organizing data into tables with rows and columns. The popular RDBMS are PostgreSQL, MySQL, MariaDB, Oracle Database, SQL Server, and IBM Db2.
* **Document databases (or NoSQL databases)**: These types of database stores data as documents. The popular document databases are MongoDB, Databricks, and Amazon DynamoDB.  

To interact with data in RDMBS, you need to use Structured Query Language or SQL.

<br>

## 🎁 Overview of SQL  

SQL is a standard language for interacting with RDBMS. It allows you to:

* Create and maintain database structures such as tables.
* Insert, update, and delete data.
* Retrieve data from tables.

<img width="998" height="496" alt="image" src="https://github.com/user-attachments/assets/8c351add-f0b7-4978-a4dc-61d53e623fb2" />
<br>

## 🎁 SQL Syntax  

* SQL keywords are NOT case sensitive: select is the same as SELECT.
* Some database systems require a semicolon at the end of each SQL statement.Semicolon is the standard way to separate each SQL statement in database systems that allow more than one SQL statement to be executed in the same call to the server.
* Reserved Words: Avoid using SQL keywords as names. If needed, wrap them in quotes (" ") or backticks (`).

Comments:  
* Single-line: -- comment
* Multi-line: /* comment */

String Values: Enclose strings in single quotes ('text').

<br>

## 🎁 What are Different SQL Commands or Queries?  

SQL commands are standardized instructions used by developers to interact with data stored in relational databases.  

To retrieve data from a SQL database, we need to write SELECT statements, which are often colloquially refered to as queries. A query in itself is just a statement which declares what data we are looking for, where to find it in the database, and optionally, how to transform it before it is returned.  

SQL commands are categorized based on their specific functionalities:

<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/25c234e5-c10a-4623-85c6-92c059ac8bd4" />

<br><br>

1️⃣ Data Definition Language - These commands are used to define the structure of database objects by creating, altering and dropping the database objects.  
2️⃣ Data Manipulation Language - A relational database can be updated with new data using data manipulation language (DML) statements.  
3️⃣ Data Query Language - Data retrieval instructions are written in the data query language (DQL), which is used to access relational databases  
4️⃣ Data Control language - DCL commands manage user access to the database by granting or revoking permissions.  
5️⃣ Transaction Control Language - TCL commands manage transactions in relational databases, ensuring data integrity and consistency. These commands are used to commit changes or roll back operations in case of errors.  
