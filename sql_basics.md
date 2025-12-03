# 🎀SQL Basics - SELECT FROM, WHERE, ORDER BY, DISTINCT, LIMIT

## 📑Table of Contents  
1. SELECT FROM
2. WHERE
3. ORDER BY
4. DISTINCT
5. LIMIT

<br>

## 1️⃣ SELECT FROM 
This is used to select data from a database.

### 🔹SELECT specific columns   
✏️ Syntax
```sql
# Select query for a specific columns
SELECT column1, column2, ...
FROM table_name;
```

📝 For example,  
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


### 🔹SELECT  *  
This is used to return all columns.  

✏️ Syntax
```sql
# Select query for all columns
SELECT * 
FROM table_name;
```
<br>

## 2️⃣ WHERE  
This is used to extract only those records that fulfil a specified condition.

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

## 3️⃣  ORDER BY  
ORDER BY sorts results ascending (ASC) or descending (DESC)

✏️Syntax
```sql
# ORDER BY to sort results
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```
📝For example,
```sql
SELECT *
FROM departments
ORDER BY departmentname;
```

💡The ORDER BY keyword sorts the records in ascending order by default.  

📝For example,
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


### 🔹 ORDER BY Several Columns  
ORDER BY can sort more than one column.  

✏️Syntax
```sql
# ORDER BY to sort several columns
SELECT column1, column2, ...
FROM table
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC], ...;
```

📝For example,
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


<br>

## 4️⃣ DISTINCT  
This is used to return only distinct (different) values, we use SELECT DISTINCT,    

✏️ Syntax
```sql
# Select query for all columns
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

📝 For example,  
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

<br>

## 5️⃣ LIMIT
LIMIT restricts the number of rows returned.  

📝 For example,
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

<br>

