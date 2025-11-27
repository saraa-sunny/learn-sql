# 🎀 Filtering Rows - WHERE, AND, OR, IN, BETWEEN, LIKE

## 📑 Table of Contents
1. WHERE
2. Logical Operators - AND, OR, NOT
3. IN
4. BETWEEN
5. LIKE
6. Comparison Operators

## 1️⃣ WHERE  
This is used to extract only those records that fulfill a specified condition.

✏️ Syntax
```sql
# WHERE query to filter records
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

📝 For example,
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

<br>

## 2️⃣ Logical Operators

### 🔹 AND
The AND operator displays a record if all the conditions are TRUE.

✏️ Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```

📝 For example,
```sql
SELECT *
FROM departments
WHERE location = 'Chicago' AND departmentname = 'Sales' ;
```

| departmentid | departmentname | location |
|--------------|----------------|----------|
| 102          | Sales          | Chicago  |
| 104          | Sales          | Chicago  |


<br>

### 🔹 OR  
The OR operator displays a record if any of the conditions are TRUE.

✏️Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```

📝For example,
```sql
SELECT *
FROM departments
WHERE location = 'Chicago' OR location = 'New York' ;
```
| departmentid | departmentname | location   |
|--------------|----------------|------------|
| 101          | Engineering    | New York   |
| 102          | Sales          | Chicago    |
| 104          | Sales          | Chicago    |
| 108          | Engineering    | Chicago    |
| 107          | HR             | New York   |
| 106          | HR             | New York   |

<br>

## 3️⃣ IN  
The IN operator in SQL is used to filter query results by checking whether a column’s value matches any value in a specified list. The IN operator is a shorthand for multiple OR conditions.   

💡 The IN operator returns true if a value is in a set of values or false otherwise.  

✏️Syntax
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```
For example,
```sql
select * 
FROM departments
WHERE departmentname IN ('HR','Sales');
```
| departmentid | departmentname | location     |
|--------------|----------------|--------------|
| 102          | Sales          | Chicago      |
| 103          | HR             | Los Angeles  |
| 105          | Sales          | Los Angelas  |
| 104          | Sales          | Chicago      |
| 107          | HR             | New York     |
| 106          | HR             | New York     |

Alternatively, this can be done using the OR operator as shown below:  
```sql
select * 
FROM departments
WHERE departmentname='HR' OR departmentname='Sales';
```

#### 📌NOT IN
The NOT operator can be combined with IN to exclude specific values in a WHERE clause.
✏️Syntax
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```
For example,
```sql
select * 
FROM departments
WHERE departmentname NOT IN ('HR','Sales');
  ```
| departmentid | departmentname | location     |
|--------------|----------------|--------------|
| 101          | Engineering    | New York     |
| 109          | Engineering    | Los Angelos  |
| 108          | Engineering    | Chicago      |


<br>

##  4️⃣ BETWEEN  
The BETWEEN operator in SQL is used to filter data within a specific range of values. It can be applied to numeric, date, or text columns. The range specified with BETWEEN is inclusive, meaning it includes both the start and end values.  

✏️Syntax
```sql
SELECT column1, column2
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```
For example,
```sql
select * 
FROM departments
WHERE departmentid BETWEEN 104 AND 107 ;
```
| departmentid | departmentname | location     |
|--------------|----------------|--------------|
| 105          | Sales          | Los Angelas  |
| 104          | Sales          | Chicago      |
| 107          | HR             | New York     |
| 106          | HR             | New York     |

<br>

## 5️⃣ LIKE  
The SQL LIKE operator is used to search for a specified pattern in a column. It is often used in the WHERE clause of the SELECT, UPDATE, or DELETE statements to filter results based on wildcard patterns.  

✏️Syntax,
```sql
SELECT column1, column2, ...
FROM table_name
WHERE columnn LIKE specified_pattern;
```

#### 📌 Wildcards in LIKE Operator
The following are the two most common wildcards used in conjunction with the LIKE operator   
| S.No | Wildcard | Definition                                             |
|------|----------|---------------------------------------------------------|
| 1    | %        | The percent sign represents zero, one, or many characters. |
| 2    | _        | The underscore represents a single number or character. |

For example,
```sql
select * 
FROM departments
WHERE departmentname LIKE 'Eng%' ;
```
| departmentid | departmentname | location     |
|--------------|----------------|--------------|
| 101          | Engineering    | New York     |
| 109          | Engineering    | Los Angelos  |
| 108          | Engineering    | Chicago      |


<br>

## 6️⃣Comparison Operators

| Operator  | Description                                             |
|-----------|---------------------------------------------------------|
| =         | Equal                                                   |
| >         | Greater than                                            |
| <         | Less than                                               |
| >=        | Greater than or equal                                   |
| <=        | Less than or equal                                      |
| <>        | Not equal. Note: In some versions of SQL may be !=     |
