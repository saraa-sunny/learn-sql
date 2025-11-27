# 🎀 GROUPING ROWS - GROUP BY and HAVING

## 1️⃣GROUP BY  
The GROUP BY statement groups rows that have the same values. The GROUP BY statement is often used with aggregate functions (COUNT(), MAX(), MIN(), SUM(), AVG()) to group the result.  

✏️Syntax
```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s);
```

💡GROUP BY is always an aggregation tool — you cannot simply SELECT all columns with GROUP BY grouping one column.   

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

<br> 

##  2️⃣HAVING  
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


💡 Difference between HAVING and WHERE
* WHERE = filter raw rows
* GROUP BY = create summary groups
* HAVING = filter final grouped summaries

 💡You must have a GROUP BY to use HAVING.
