# 🎀 SELECT


This is used to select data from a database.

## 1️⃣ SELECT specific columns 
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

<br>

## 2️⃣ SELECT *  
This is used to return all columns.  

✏️ Syntax
```sql
# Select query for all columns
SELECT * 
FROM table_name;
```
<br>

## 3️⃣ SELECT DISTINCT    
This is used to return only distinct (different) values.  

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
