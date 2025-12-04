# 🎀 SQL JOINs - INNER, LEFT, RIGHT, FULL OUTER, SELF, CROSS  

A JOIN clause is used to combine data from two or more tables, based on a related column between them.They are one of the most important concepts in SQL for analytics.  

<br>

## Different Types of SQL JOINs
Here are the main types of the JOINs in SQL:

* (INNER) JOIN: Returns records that have matching values in both tables
* LEFT (OUTER) JOIN: Returns all records from the left table, and the matched records from the right table
* RIGHT (OUTER) JOIN: Returns all records from the right table, and the matched records from the left table
* FULL (OUTER) JOIN: Returns all records when there is a match in either left or right table

<img width="1263" height="233" alt="image" src="https://github.com/user-attachments/assets/d79f6378-12a9-4b25-9864-1ff313432698" />
(image from w3schools(https://www.w3schools.com/))    

<br>
<br>

## 📘 Example Tables We'll Use  
### 🏢departments
| departmentid | departmentname | location     |
|--------------|----------------|--------------|
| 101          | Engineering    | New York     |
| 102          | Sales          | Chicago      |
| 103          | HR             | Los Angeles  |
| 104          | Engineering    | Los Angelas  |
| 105          | Sales          | New York     |
| 106          | HR             | New York     |
| 107          | HR             | Chicago      |

### 📁 projects  
| projectid | projectname        | departmentid | budget     | startdate   | enddate     |
|-----------|---------------------|---------------|------------|-------------|-------------|
| 201       | Website Revamp      | 101           | 150000.00  | 2023-01-01  | 2023-12-31  |
| 202       | Sales Automation    | 102           | 80000.00   | 2022-05-01  | 2022-12-31  |
| 203       | Employee Training   | 103           | 30000.00   | 2023-03-01  | 2025-01-12  |
| 204       | Website Build       | 104           | 55000.00   | 2023-06-09  | 2024-01-12  |
| 205       | Sales Automation    | 105           | 120000.00  | 2023-12-04  | 2024-01-12  |
| 206       | Employee Training   | 106           | 40000.00   | 2023-03-09  | 2025-01-12  |

### 👥 employee_projects
| employeeid | projectid | role            |
|------------|-----------|-----------------|
| 1          | 201       | Developer       |
| 2          | 202       | Sales Lead      |
| 3          | 203       | QA Tester       |
| 4          | 204       | HR Specialist   |
| 5          | 205       | Sales Associate |

<br>

## 1️⃣ INNER JOIN (most used)    
The INNER JOIN keyword selects all rows  that have matching values in both tables.   
This  will create the result set by combining all rows from both the tables where the condition satisfies.  

✏️Syntax  
```sql
SELECT
  column1,
  column2
FROM
  table1
  INNER JOIN table2 ON condition;
```

In this syntax:  
* First, specify the first table in the FROM clause (table1)
* Second, provide the second table you want to merge rows with the first table in the INNER JOIN clause (table2).
* Third, define a condition for matching rows between two tables after the ON keyword. This condition is known as a join condition.  

For example,
```sql
select d.departmentid , d.departmentname, p.projectname
FROM departments d
INNER JOIN projects p
ON d.departmentid = p.departmentid;
```


✔ You are asking SQL:  
Give me each department matched with its project.

| departmentid | departmentname | projectname       |
| ------------ | -------------- | ----------------- |
| 101          | Engineering    | Website Revamp    |
| 102          | Sales          | Sales Automation  |
| 103          | HR             | Employee Training |
| 106          | HR             | Website Revamp    |
| 105          | Sales          | Sales Automation  |
| 104          | Engineering    | Website Build     |


Here projects and departments tables have the same department_id column. The database system does not know which one to select.  
To avoid this error, you need to explicitly tell the database system which table you want to retrieve the value from the department_id column.
To do that, you can reference the column using the following syntax:
```sql
table_name.column_name
```

### 📌Using table aliases   
SQL allows you to temporarily assign a new name to a table during the execution of a query. This new name is called a table alias.  

Syntax
```sql
table_name AS table_alias
```

The AS keyword is optional, so you can make it shorter like this:
```sql
table_name table_alias
```

When referencing a column, you can use the table alias instead of the table name:
```sql
table_alias.column_name
```

Now look at the query again,
```sql
select d.departmentid , d.departmentname, p.projectname
FROM departments d
INNER JOIN projects p
ON d.departmentid = p.departmentid;
```
And this query makes sense now 😁 !!

### 📌 Joining three tables
```sql
select e.employeeid,e.role,p.projectname,d.departmentname
FROM employee_projects e
INNER JOIN projects p ON e.projectid = p.projectid
INNER JOIN departments d ON d.departmentid = p.departmentid;
```
| employeeid | role            | projectname       | departmentname |
| ---------- | --------------- | ----------------- | -------------- |
| 1          | Developer       | Website Revamp    | Engineering    |
| 2          | Sales Lead      | Sales Automation  | Sales          |
| 3          | QA Tester       | Employee Training | HR             |
| 4          | HR Specialist   | Website Build     | Engineering    |
| 5          | Sales Associate | Sales Automation  | Sales          |

This query joins employees, projects, and departments to show which employee works on which project and their role.

💡 JOIN and INNER JOIN will return the same result.    
INNER is the default join type for JOIN, so when you write JOIN the parser actually writes INNER JOIN.

<br>

## 2️⃣LEFT JOIN  

A LEFT JOIN returns all rows from the left table, along with matching rows from the right table. If there is no match, NULL values are returned for columns from the right table.  
It is also known as LEFT OUTER JOIN.

✏️ Syntax
```sql
SELECT
  column1,
  column2
FROM left_table
LEFT JOIN right_table ON condition;
```
In this syntax:
* First, specify the left table in the FROM clause (left_table)
* Second, provide the right table you want to merge rows with the left table in the LEFT JOIN clause (right_table).
* Third, define a condition for matching rows between two tables after the ON keyword.

The left join includes all rows from the left table and matching rows from the right table; if there are no matching rows, it uses null for columns of the right table.  

⚠️Unlike an INNER JOIN clause, the LEFT JOIN clause always includes all rows from the left table.

For example,
```sql
SELECT 
    d.departmentid,
    d.departmentname,
    p.projectname
FROM departments d
LEFT JOIN projects p
    ON d.departmentid = p.departmentid;
```
LEFT JOIN returns all rows from the left table (departments) and matches them with projects when available.  
If a department has no projects, the project columns return NULL instead of being excluded.  
| departmentid | departmentname | projectname       |
| ------------ | -------------- | ----------------- |
| 101          | Engineering    | Website Revamp    |
| 102          | Sales          | Sales Automation  |
| 103          | HR             | Employee Training |
| 106          | HR             | Website Revamp    |
| 105          | Sales          | Sales Automation  |
| 104          | Engineering    | Website Build     |
| 107          | HR             | *(NULL)*          |


🧠 Use a LEFT JOIN clause and a WHERE clause with the IS NULL condition to find unmatching rows in the left table.

<br>

## 3️⃣ RIGHT JOIN  

RIGHT JOIN returns all the rows of the table on the right side of the join and matching rows for the table on the left side of the join.It is very similar to LEFT JOIN for the rows for which there is no matching row on the left side, the result-set will contain null.  
RIGHT JOIN is also known as RIGHT OUTER JOIN.  

Syntax
```sql
SELECT
  column1,
  column2
FROM left_table
RIGHT JOIN right_table ON condition;
```
In this syntax:  
* First, specify the first table (left_table) in the FROM clause.
* Second, provide the second table (right_table) in the RIGHT JOIN clause.
* Third, specify a condition for matching rows between the first and second tables after the ON keyword.

A RIGHT JOIN returns:  
✔ all rows from the right table  
✔ matching rows from the left table  
❗ If a row on right side has no match on left side → NULL on left side  

🧠 The RIGHT JOIN and RIGHT OUTER JOIN are the same because the OUTER keyword is optional.  


For example,
```sql
SELECT e.employeeid, e.role ,p.projectname 
FROM projects p
RIGHT JOIN employee_projects e
ON e.projectid = p.projectid;
```

| employeeid | role            | projectname       |
| ---------- | --------------- | ----------------- |
| 1          | Developer       | Website Revamp    |
| 2          | Sales Lead      | Sales Automation  |
| 3          | QA Tester       | Employee Training |
| 4          | HR Specialist   | Website Build     |
| 5          | Sales Associate | Sales Automation  |

🧠 Use a RIGHT JOIN clause to find unmatching rows in the right table.
```sql
SELECT
  column1,
  column2
FROM
  left_table
  RIGHT JOIN right_table ON right_table.column1 = left_table_column2
WHERE column2 IS NULL;
```
For example,
```sql
```

<br>

## 4️⃣ FULL JOIN  

The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or right (table2) table records.  
Syntax  
```sql
SELECT
  column1,
  column2
FROM
  table1
  FULL OUTER JOIN table2 ON condition;
```
In this syntax:
* First, provide the first table (table1) in the FROM clause.
* Second, specify the second table (table2) you want to join with the first table (table1) after the FULL OUTER JOIN keywords.
* Third, define a condition for matching rows between two tables. You can combine multiple conditions using the AND and OR operators.  

Technically, a FULL OUTER JOIN is a combination of a LEFT JOIN and a RIGHT JOIN.  

In simple words,  
The full outer join includes rows from both tables whether or not the rows have matching rows from another table. It uses null for columns of rows in the table that do not have matching rows in another table.  

For example,  
```sql
SELECT d.departmentid, d.departmentname, p.projectname
FROM departments d
FULL JOIN projects p
ON d.departmentid = p.departmentid;
```
| departmentid | departmentname | projectname       |
| ------------ | -------------- | ----------------- |
| 101          | Engineering    | Website Revamp    |
| 102          | Sales          | Sales Automation  |
| 103          | HR             | Employee Training |
| 106          | HR             | Website Revamp    |
| 105          | Sales          | Sales Automation  |
| 104          | Engineering    | Website Build     |
| 107          | HR             | NULL              |

<br>

##  5️⃣ SELF JOIN  

Typically, you use a join such as inner join, left join, and right join to merge rows from two tables based on a condition.

However, a join doesn’t have to involve multiple tables. You can use a join to compare rows within the same table. In this case, you join a table to itself that forms a self-join.  

A self-join is a join that compares the rows within the same table. A self-join uses an inner join, left join, or right join that joins a table to itself. It uses table aliases to treat the same table as separate tables within the same query.  

```sql
SELECT
  select_list
FROM
  table1 t1
  INNER JOIN table1 AS t2 ON t1.column1 = t2.column2;
```

🧠 In this syntax, you can use the LEFT JOIN, RIGHT JOIN, and FULL JOIN instead of the INNER JOIN.

For example,
```sql
SELECT 
	  p1.projectname,
    p1.projectid,  
    p1.departmentid
FROM projects p1
JOIN projects p2
    ON p1.projectname = p2.projectname
	AND p1.projectid <> p2.projectid
ORDER BY p1.projectname;
```
| projectname       | projectid | departmentid |
|-------------------|-----------|---------------|
| Sales Automation  | 202       | 102           |
| Sales Automation  | 205       | 105           |
| Website Revamp    | 201       | 101           |
| Website Revamp    | 206       | 106           |

<br>

## 6️⃣ CROSS JOIN  

The CROSS JOIN clause allows you to create combinations of all rows from two tables.

Syntax
```sql
SELECT
  select_list
FROM
  table1
  CROSS JOIN table2;
```

Unlike a left join, right join, inner join, and full join, the cross join does not have a condition.  

The CROSS JOIN clause merges every row from the first table (table1) with every row in the second table (table2). It returns a result set that includes all possible combinations of the rows in both tables.  

The result set of a CROSS JOIN is often called the Cartesian product of two tables.

For example,
```sql
SELECT 
	e.employeeid,
	e.role,
	p.projectid,
	p.projectname
FROM employee_projects e
CROSS JOIN projects p;
```
| roleid | rolename        | projectid | projectname      |
|--------|------------------|-----------|-------------------|
| 1      | Developer        | 201       | Website Revamp    |
| 1      | Developer        | 202       | Sales Automation  |
| 1      | Developer        | 203       | Employee Training |
| 1      | Developer        | 206       | Website Revamp    |
| 1      | Developer        | 205       | Sales Automation  |
| 1      | Developer        | 204       | Website Build     |
| 2      | Sales Lead       | 201       | Website Revamp    |
| 2      | Sales Lead       | 202       | Sales Automation  |
| 2      | Sales Lead       | 203       | Employee Training |
| 2      | Sales Lead       | 206       | Website Revamp    |
| 2      | Sales Lead       | 205       | Sales Automation  |
| 2      | Sales Lead       | 204       | Website Build     |
| 3      | QA Tester        | 201       | Website Revamp    |
| 3      | QA Tester        | 202       | Sales Automation  |
| 3      | QA Tester        | 203       | Employee Training |
| 3      | QA Tester        | 206       | Website Revamp    |
| 3      | QA Tester        | 205       | Sales Automation  |
| 3      | QA Tester        | 204       | Website Build     |
| 4      | HR Specialist    | 201       | Website Revamp    |
| 4      | HR Specialist    | 202       | Sales Automation  |
| 4      | HR Specialist    | 203       | Employee Training |
| 4      | HR Specialist    | 206       | Website Revamp    |
| 4      | HR Specialist    | 205       | Sales Automation  |
| 4      | HR Specialist    | 204       | Website Build     |
| 5      | Sales Associate  | 201       | Website Revamp    |
| 5      | Sales Associate  | 202       | Sales Automation  |
| 5      | Sales Associate  | 203       | Employee Training |
| 5      | Sales Associate  | 206       | Website Revamp    |
| 5      | Sales Associate  | 205       | Sales Automation  |
| 5      | Sales Associate  | 204       | Website Build     |


