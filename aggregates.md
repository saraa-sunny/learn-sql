# 🎀 Aggregate Functions - MIN, MAX, COUNT, SUM, AVG

Aggregate functions are often used with the GROUP BY clause of the SELECT statement. The GROUP BY clause splits the result-set into groups of values and the aggregate function can be used to return a single value for each group.  

## 📑 Table of Contents
1. MIN()
2. MAX()
3. COUNT()
4. SUM()
5. AVG()

<br>

### ⚙️ Sample Data: projects Table
This table contains sample projects for different departments.  

   | projectid | projectname        | departmentid | budget     | startdate    | enddate      |
|-----------|---------------------|---------------|------------|--------------|--------------|
| 201       | Website Revamp      | 101           | 150000.00  | 2023-01-01   | 2023-12-31   |
| 202       | Sales Automation    | 102           | 80000.00   | 2022-05-01   | 2022-12-31   |
| 203       | Employee Training   | 103           | 30000.00   | 2023-03-01   | 2025-01-12   |
| 207       | Website Revamp      | 107           | 75000.00   | 2023-10-01   | 2025-01-12   |
| 206       | Website Revamp      | 106           | 55000.00   | 2023-06-09   | 2024-01-12   |
| 205       | Sales Automation    | 105           | 120000.00  | 2023-12-04   | 2024-01-12   |
| 204       | Employee Training   | 104           | 40000.00   | 2023-03-09   | 2025-01-12   |

<br>

## 1️⃣ MIN()  
The MIN() function returns the smallest value of the selected column.  

Syntax
```sql
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```

For example,
```sql
select MIN(budget)
FROM projects
WHERE projectname='Employee Training' ;
```
| min       |
|-----------|
| 30000.00  |


#### 📌Set Column Name (Alias)
When you use aggregate function, the returned column will not have a descriptive name.  

To give the column a descriptive name, use the AS keyword:    

For example,
```sql
select MIN(budget) as lowestbudget
FROM projects
WHERE projectname='Employee Training' ;
```
| lowestbudget |
|-------------|
| 30000.00    |


<br>

## 2️⃣ MAX()

Syntax
```sql
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```

<br>

## 3️⃣ COUNT()  

The COUNT() function returns the number of rows that matches a specified criterion.
Syntax
```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```


<br>

## 4️⃣ SUM()
The SUM() function returns the total sum of a numeric column.
Syntax
```sql
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```


<br>

## 5️⃣ AVG()  
The AVG() function returns the average value of a numeric column.
Syntax
```sql
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```

<br>

### 🧠 Quick Rule to Remember  
Whenever you use SUM, COUNT, AVG, MIN, MAX:  
👉 Every other column in SELECT must be in GROUP BY.
