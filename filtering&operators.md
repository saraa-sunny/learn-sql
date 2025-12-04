# 🎀 Filtering & Operators 

## 📑 Table of Contents
1. AND,OR,NOT
2. IN
3. NOT IN
4. BETWEEN
5. LIKE
6. IS NULL / IS NOT NULL

<br>

## 1️⃣ AND/ OR/ NOT  

### 🔹AND

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


### 🔹 NOT 
The NOT operator is used in combination with other operators to give the opposite result, also called the negative result.

✏️Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

📝For example,
```sql
SELECT *
FROM departments
WHERE NOT departmentname = 'Sales' ;
```

| departmentid | departmentname | location     |
|--------------|----------------|--------------|
| 101          | Engineering    | New York     |
| 103          | HR             | Los Angeles  |
| 106          | HR             | New York     |
| 104          | Engineering    | Los Angelas  |
| 107          | HR             | Chicago      |


####  📌 NOT LIKE, NOT BETWEEN, NOT IN etc..
📝For example,
```sql
SELECT *
FROM departments
WHERE departmentid NOT BETWEEN 102 AND 104 ;
```
📝For example,
```sql
SELECT *
FROM projects
WHERE projectname NOT LIKE 'W%';
```

<br>

## 2️⃣ IN  

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
<br>

## 3️⃣NOT IN  

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

## 6️⃣ IS NULL / IS NOT NULL  

NULL is a marker that indicates unknown or missing data in the database.  
A database field with a NULL value is a field with no value.  

For example, if you don’t know the phone numbers of employees when you save the employee’s records, you can use NULL to represent unknown phone numbers.

📌 A NULL value is different from a zero value or a field that contains spaces. A field with a NULL value is one that has been left blank during record creation!

📌 An alternative to NULL values in your database is to have data-type appropriate default values, like 0 for numerical data, empty strings for text data, etc.

🧠 It is not possible to test for NULL values with comparison operators, such as =, <, or <>. We will have to use the IS NULL and IS NOT NULL operators instead. 

🧠 You cannot use the equal to (=) to check if a value is NULL or not.  

### 🔹 IS NULL  
The IS NULL operator is used to test for empty values (NULL values).
```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
```

For example,
```sql
SELECT *
FROM projects
WHERE projectname IS NOT NULL;
```

The IS NULL operator returns true if the result of the expression is NULL. Otherwise, it returns false.  


📌 Always use IS NULL to look for NULL values.  

### 🔹 IS NOT NULL  
The IS NOT NULL operator is used to test for non-empty values (NOT NULL values).

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```
The IS NOT NULL returns false if the expression is NULL or true otherwise.

For example,
```sql
SELECT *
FROM projects
WHERE projectname IS NOT NULL;
```

<br>

## Comparison Operators

| Operator  | Description                                             |
|-----------|---------------------------------------------------------|
| =         | Equal                                                   |
| >         | Greater than                                            |
| <         | Less than                                               |
| >=        | Greater than or equal                                   |
| <=        | Less than or equal                                      |
| <>        | Not equal. Note: In some versions of SQL may be !=     |
