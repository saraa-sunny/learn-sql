# SQL  Basics 

## 🎀SELECT
This is used to select data from a database.
```sql
# Select query for a specific columns
SELECT column1, column2, ...
FROM table_name;
```
For example,  
```sql
SELECT departmentname
FROM departments;
```
| departmentname |
|----------------|
| Engineering    |
| Sales          |
| HR             |
| Sales          |
| Sales          |

#### 🔹SELECT *  
This is used to return all columns
```sql
# Select query for all columns
SELECT * 
FROM table_name;
```

#### 🔹SELECT DISTINCT    
This is used to return only distinct (different) values.

```sql
# Select query for all columns
SELECT DISTINCT column1, column2, ...
FROM table_name;
```
For example,
```sql
SELECT DISTINCT location
FROM departments;
```

| location     |
|--------------|
| Chicago      |
| Los Angeles  |
| New York     |
| Los Angelas  |
| Los Angelos  |



## 🎀 WHERE
This is used to extract only those records that fulfill a specified condition.
```sql
# WHERE query to filter records
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
For example,
```sql
SELECT *
FROM departments
WHERE departmentname = 'HR';
```
| departmentid | departmentname | location     |
|--------------|----------------|--------------|
| 103          | HR             | Los Angeles  |
| 107          | HR             | New York     |
| 106          | HR             | New York     |

#### 🔹Operators in The WHERE Clause
| Operator  | Description                                             |
|-----------|---------------------------------------------------------|
| =         | Equal                                                   |
| >         | Greater than                                            |
| <         | Less than                                               |
| >=        | Greater than or equal                                   |
| <=        | Less than or equal                                      |
| <>        | Not equal. Note: In some versions of SQL may be !=     |
| BETWEEN   | Between a certain range                                 |
| LIKE      | Search for a pattern                                    |
| IN        | To specify multiple possible values for a column       |

## 🎀 AND, OR, NOT

## 🎀 ORDER BY
ORDER BY sorts results ascending (ASC) or descending (DESC)
```sql
# ORDER BY to sort results
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```
For example,
```sql
SELECT *
FROM departments
ORDER BY departmentname;
```

💡The ORDER BY keyword sorts the records in ascending order by default.  

For example,
```sql
SELECT *
FROM departments
ORDER BY location DESC;
```
| departmentid | departmentname | location     |
|--------------|----------------|--------------|
| 101          | Engineering    | New York     |
| 107          | HR             | New York     |
| 106          | HR             | New York     |
| 109          | Engineering    | Los Angelos  |
| 103          | HR             | Los Angeles  |
| 105          | Sales          | Los Angelas  |
| 104          | Sales          | Chicago      |
| 108          | Engineering    | Chicago      |
| 102          | Sales          | Chicago      |

#### 🔹 ORDER BY Several Columns
ORDER BY can sort more than one column.  

```sql
# ORDER BY to sort several columns
SELECT column1, column2, ...
FROM table
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC], ...;
```
For example,
```sql
SELECT *
FROM departments
ORDER BY departmentname ASC, location DESC;
```
| departmentid | departmentname | location     |
|--------------|----------------|--------------|
| 101          | Engineering    | New York     |
| 109          | Engineering    | Los Angelos  |
| 108          | Engineering    | Chicago      |
| 106          | HR             | New York     |
| 107          | HR             | New York     |
| 103          | HR             | Los Angeles  |
| 105          | Sales          | Los Angelas  |
| 102          | Sales          | Chicago      |
| 104          | Sales          | Chicago      |

## 🎀 LIMIT  
LIMIT restricts the number of rows returned.  
For example,
```sql
SELECT *
FROM departments
LIMIT 3;
```
| departmentid | departmentname | location     |
|--------------|----------------|--------------|
| 101          | Engineering    | New York     |
| 102          | Sales          | Chicago      |
| 103          | HR             | Los Angeles  |

## 🎀 GROUP BY
The GROUP BY statement groups rows that have the same values.
The GROUP BY statement is often used with aggregate functions (COUNT(), MAX(), MIN(), SUM(), AVG()) to group the result.

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s);
```

💡GROUP BY is always an aggregation tool — you cannot simply SELECT all columns with GROUP BY  grouping one column.   
💡Use aggregate functions (COUNT, SUM, MAX, MIN, ARRAY_AGG) to include other columns.   

For example,
```sql
SELECT departmentname, COUNT(departmentid) as emp_count
FROM departments
WHERE location = 'Chicago'
GROUP BY departmentname;
```
| departmentname | emp_count |
|----------------|-----------|
| Engineering    | 1         |
| Sales          | 2         |


## 🎀 HAVING  

The HAVING clause filters the results of grouped data after using the GROUP BY clause. It is used with aggregate functions such as SUM(), COUNT(), or AVG() to display only those groups that meet specific conditions.
```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
```
For example,
```sql
SELECT departmentname, COUNT(departmentid) as emp_count
FROM departments
WHERE location = 'Chicago'
GROUP BY departmentname
HAVING
    COUNT(EmpID) > 0;
```
| departmentname | emp_count |
|----------------|-----------|
| Engineering    | 1         |
| Sales          | 2         |

