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

<br>

##  4️⃣ BETWEEN

<br>

## 5️⃣ LIKE

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
