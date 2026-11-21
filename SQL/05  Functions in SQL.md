# ⚙️ SQL Functions

> [!abstract] What are SQL Functions? SQL Functions are **built-in operations** that perform calculations or transformations on data and return a result.
> 
> 📚 **References:**
> 
> - All Functions → [TechOnTheNet MySQL Functions](https://www.techonthenet.com/mysql/functions/index.php)
> - Aggregate Functions → [MySQL 8.0 Official Docs](https://dev.mysql.com/doc/refman/8.0/en/aggregate-functions.html)

---

## 🗂️ Types Covered

|Type|Functions|
|---|---|
|**Aggregate**|`COUNT`, `AVG`, `SUM`, `MAX`, `MIN`|
|**String**|`UCASE`, `CHAR_LENGTH`, `CONCAT`, `FORMAT`, `LEFT`|

---

## 📊 Aggregate Functions

> [!info] What are Aggregate Functions? Aggregate functions **perform a calculation on a set of rows** and return a **single summary value**. Commonly used with `GROUP BY`.

---

### 🔢 COUNT — Total Number of Rows

```sql
SELECT COUNT(*) FROM employee;
```

> [!example] Output
> 
> |COUNT(*)|
> |---|
> |13|
> 
> ➡️ Returns the **total number of rows** in the employee table.

---

### 📐 AVG — Average Value

```sql
-- Average salary of ALL employees
SELECT AVG(salary) FROM employee;
```

> [!example] Output
> 
> |AVG(salary)|
> |---|
> |2230769.2308|

```sql
-- Average salary of MANAGERS only
SELECT AVG(salary)
FROM employee
WHERE job_desc = "MANAGER";
```

> [!example] Output
> 
> |AVG(salary)|
> |---|
> |2766666.6667|
> 
> ➡️ `WHERE` filters rows **before** the average is calculated.

---

### ➕ SUM — Total of a Column

```sql
-- Total salary paid to all ANALYSTs
SELECT SUM(salary)
FROM employee
WHERE job_desc = "ANALYST";
```

> [!example] Output
> 
> |SUM(salary)|
> |---|
> |0|
> 
> ➡️ Returns `0` or `NULL` here because there are **no ANALYST** entries in the current table.

---

### 🔝 MAX — Highest Value (with Subquery)

```sql
-- Display the full row of the employee with the HIGHEST salary
SELECT * FROM employee
WHERE salary = (SELECT MAX(salary) FROM employee);
```

> [!example] Output
> 
> |emp_id|ename|job_desc|salary|
> |---|---|---|---|
> |9|Raghu|CEO|8000000|
> 
> ➡️ The **inner query** finds the max salary, the **outer query** fetches that employee's full record.

> [!tip] Subquery Pattern `WHERE salary = (SELECT MAX(salary) FROM employee)` is a classic **subquery** pattern to find the row with the highest value.

---

### 🔽 MIN — Lowest Value

```sql
SELECT MIN(salary) FROM employee;
```

> [!example] Output
> 
> |MIN(salary)|
> |---|
> |1000000|
> 
> ➡️ Returns the **lowest salary** across all employees.

---

## 🔤 String Functions

> [!info] What are String Functions? String functions **manipulate or inspect text** values stored in columns.

---

### 🔠 UCASE — Convert to Uppercase

```sql
SELECT UCASE(ename), salary
FROM employee;
```

> [!example] Output
> 
> |UCASE(ename)|salary|
> |---|---|
> |RAM|1000000|
> |HARINI|2500000|
> |GEORGE|2000000|
> |RAMYA|1300000|
> |…|…|
> 
> ➡️ Converts every employee name to **UPPERCASE** in the result (does not change data in the table).

---

### 📏 CHAR_LENGTH — Length of a String

```sql
SELECT ename, CHAR_LENGTH(ename)
FROM employee;
```

> [!example] Output
> 
> |ename|CHAR_LENGTH(ename)|
> |---|---|
> |Ram|3|
> |Harini|6|
> |George|6|
> |Abinaya|7|
> |…|…|
> 
> ➡️ Returns the **number of characters** in each name.

---

### 🔗 CONCAT — Join Strings Together

```sql
-- Adds "Rs." prefix to the salary column
SELECT ename, CONCAT("Rs.", salary)
FROM employee;
```

> [!example] Output
> 
> |ename|CONCAT("Rs.", salary)|
> |---|---|
> |Ram|Rs.1000000|
> |Harini|Rs.2500000|
> |Raghu|Rs.8000000|
> |…|…|
> 
> ➡️ `CONCAT` joins two or more strings together. Here it prepends `"Rs."` to every salary value.

---

### 💱 CONCAT + FORMAT — Formatted Number with Commas

```sql
-- Formats salary with commas and adds "Rs." prefix
SELECT ename, CONCAT("Rs.", FORMAT(salary, 0))
FROM employee;
```

> [!example] Output
> 
> |ename|CONCAT("Rs.", FORMAT(salary, 0))|
> |---|---|
> |Ram|Rs.1,000,000|
> |Harini|Rs.2,500,000|
> |Raghu|Rs.8,000,000|
> |…|…|
> 
> ➡️ `FORMAT(salary, 0)` adds **comma separators** to large numbers. The second argument `0` means **0 decimal places**.

> [!note] FORMAT Second Argument
> 
> |Value|Meaning|
> |---|---|
> |`0`|No decimal places → `1,000,000`|
> |`2`|Two decimal places → `1,000,000.00`|

---

### ✂️ LEFT — Extract First N Characters

```sql
-- Returns only the first 4 characters of job_desc
SELECT ename, LEFT(job_desc, 4)
FROM employee;
```

> [!example] Output
> 
> |ename|LEFT(job_desc, 4)|
> |---|---|
> |Ram|ADMI|
> |Harini|MANA|
> |George|SALE|
> |Meena|HR|
> |Raghu|CEO|
> |…|…|
> 
> ➡️ `LEFT(column, n)` extracts the **first n characters** from the left of the string. If the string is shorter than n, it returns the full string.

---

## 📋 Complete Functions Summary

|Function|Type|Purpose|Example|
|---|---|---|---|
|`COUNT(*)`|Aggregate|Count total rows|`COUNT(*) → 13`|
|`AVG(col)`|Aggregate|Average of values|`AVG(salary) → 2230769`|
|`SUM(col)`|Aggregate|Sum of values|`SUM(salary) → total`|
|`MAX(col)`|Aggregate|Highest value|`MAX(salary) → 8000000`|
|`MIN(col)`|Aggregate|Lowest value|`MIN(salary) → 1000000`|
|`UCASE(col)`|String|Convert to uppercase|`UCASE("ram") → RAM`|
|`CHAR_LENGTH(col)`|String|Length of string|`CHAR_LENGTH("Ram") → 3`|
|`CONCAT(s1, s2)`|String|Join strings|`CONCAT("Rs.",100) → Rs.100`|
|`FORMAT(col, d)`|String|Format number with commas|`FORMAT(1000000,0) → 1,000,000`|
|`LEFT(col, n)`|String|First n characters|`LEFT("MANAGER",4) → MANA`|

---

> [!success] Exam Ready ⭐
> 
> - **Aggregate functions** → work on **multiple rows**, return **one value** (`COUNT`, `AVG`, `SUM`, `MAX`, `MIN`)
> - **String functions** → work on **text columns**, transform or inspect strings
> - `FORMAT(col, 0)` → adds **commas** to numbers, `0` = no decimal places
> - `LEFT(col, n)` → extracts **n characters** from the **start** of a string
> - `MAX`/`MIN` inside a **subquery** is a powerful pattern to find extreme rows

---

