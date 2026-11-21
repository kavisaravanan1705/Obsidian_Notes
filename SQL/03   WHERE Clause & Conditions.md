# 🔍 WHERE Clause & Conditions

> [!abstract] What is WHERE? `WHERE` is used to **filter records**. Rows are returned only if they satisfy the given **condition**.

---

## 🏗️ Employee Table Setup

> [!example]- Click to expand — Employee Table Creation & Data
> 
> ```sql
> CREATE TABLE employee (
>     emp_id   INT PRIMARY KEY,
>     ename    VARCHAR(30),
>     job_desc VARCHAR(20),
>     salary   INT
> );
> 
> INSERT INTO employee VALUES (1,  'Ram',     'ADMIN',    1000000);
> INSERT INTO employee VALUES (2,  'Harini',  'MANAGER',  2500000);
> INSERT INTO employee VALUES (3,  'George',  'SALES',    2000000);
> INSERT INTO employee VALUES (4,  'Ramya',   'SALES',    1300000);
> INSERT INTO employee VALUES (5,  'Meena',   'HR',       2000000);
> INSERT INTO employee VALUES (6,  'Ashok',   'MANAGER',  3000000);
> INSERT INTO employee VALUES (7,  'Abdul',   'HR',       2000000);
> INSERT INTO employee VALUES (8,  'Ramya',   'ENGINEER', 1000000);
> INSERT INTO employee VALUES (9,  'Raghu',   'CEO',      8000000);
> INSERT INTO employee VALUES (10, 'Arvind',  'MANAGER',  2800000);
> INSERT INTO employee VALUES (11, 'Akshay',  'ENGINEER', 1000000);
> INSERT INTO employee VALUES (12, 'John',    'ADMIN',    2200000);
> INSERT INTO employee VALUES (13, 'Abinaya', 'ENGINEER', 2100000);
> ```

---

## 📐 WHERE — Syntax

```sql
SELECT column1, column2, ...
FROM   table_name
WHERE  condition;
```

---

## ⚙️ Operators in WHERE Condition

| Operator     | Meaning                             |
| ------------ | ----------------------------------- |
| `=`          | Equal                               |
| `>`          | Greater than                        |
| `<`          | Less than                           |
| `>=`         | Greater than or equal               |
| `<=`         | Less than or equal                  |
| `<>` or `!=` | Not equal                           |
| `BETWEEN`    | Between a certain range (inclusive) |
| `LIKE`       | Search for a pattern                |
| `IN`         | Match any value from a list         |
| `NOT`        | Negation                            |

> [!tip] Combining Operators Use **`AND`** / **`OR`** to combine multiple conditions together.

---

## 🧪 WHERE — Query Examples

### 🔹 Equal ( `=` )

```sql
-- Fetch all employees named 'Ramya'
SELECT * FROM employee
WHERE ename = 'Ramya';
```

### 🔹 Greater Than ( `>` )

```sql
-- Employees with salary more than 20,00,000
SELECT emp_id, ename, salary FROM employee
WHERE salary > 2000000;
```

### 🔹 AND — Multiple Conditions

```sql
-- Managers earning less than 26,00,000
SELECT emp_id, ename, salary FROM employee
WHERE salary < 2600000 AND job_desc = 'MANAGER';
```

### 🔹 OR — Either Condition

```sql
-- Employees in ADMIN or HR department
SELECT * FROM employee
WHERE job_desc = 'ADMIN' OR job_desc = 'HR';
-- ⚠️ This works, but IN() is a much cleaner choice (see below)
```

### 🔹 IN — Match from a List

```sql
-- Cleaner alternative to multiple OR conditions
SELECT * FROM employee
WHERE job_desc IN ('ADMIN', 'HR');
```

### 🔹 NOT IN — Exclude Values

```sql
-- Everyone except MANAGER and CEO
SELECT * FROM employee
WHERE job_desc NOT IN ('MANAGER', 'CEO');
```

### 🔹 BETWEEN — Range Filter

```sql
-- Employees with salary between 20L and 30L, show only 5 rows
SELECT * FROM employee
WHERE salary BETWEEN 2000000 AND 3000000
LIMIT 5;          -- 🔢 Limits the number of records shown
```

### 🔹 LIMIT — Restrict Rows Returned

```sql
SELECT * FROM employee
LIMIT 5;          -- ⚠️ Syntax may differ in Oracle / SQL Server
```

---

## 🃏 LIKE & Wildcards

> [!info] What is LIKE? `LIKE` is used with `WHERE` to **search for a specific pattern** in a column. It works alongside **wildcards**:
> 
> |Wildcard|Represents|
> |---|---|
> |`%`|Zero or more characters|
> |`_`|Exactly one character|

### 🔹 Starts With — `A%`

```sql
-- Names starting with 'A'
SELECT * FROM employee
WHERE ename LIKE 'A%';
```

### 🔹 Starts With & Ends With — `R%a`

```sql
-- Names starting with 'R' AND ending with 'a'
SELECT * FROM employee
WHERE ename LIKE 'R%a';
```

### 🔹 Contains — `%I%`

```sql
-- Names containing the letter 'I' anywhere
SELECT * FROM employee
WHERE ename LIKE '%I%';
```

### 🔹 Character Position — `__I%`

```sql
-- Names where 'I' is the 3rd character (_ = exactly one char)
SELECT * FROM employee
WHERE ename LIKE '__I%';
```

### 🔹 Escape Character — `\\`

```sql
-- Names starting with literal 'R%' (% as actual character)
SELECT * FROM employee
WHERE ename LIKE 'R\\%';   -- \\ is the escape character
```

---

## ✏️ UPDATE — Modifying Data

> [!warning] Always use WHERE with UPDATE! Without a `WHERE` clause, **ALL rows** in the table will be updated.

### 🔹 Update ALL Rows (⚠️ Dangerous without WHERE)

```sql
-- Updates job_desc of ALL rows to "Analyst" (when safe update is disabled)
UPDATE employee
SET job_desc = "Analyst";
```

### 🔹 Update by Condition

```sql
-- Changes all 'Engineer' job roles to 'Analyst'
UPDATE employee
SET job_desc = "Analyst"
WHERE job_desc = "Engineer";
```

### 🔹 Update a Specific Row

```sql
-- Updates only the employee with emp_id = 1
UPDATE employee
SET job_desc = "Analyst"
WHERE emp_id = 1;
```

---

## 🗑️ DELETE — Removing Data

> [!danger] Always use WHERE with DELETE! Without `WHERE`, **every single row** in the table is deleted permanently.

### 🔹 Delete ALL Rows (☠️ Irreversible)

```sql
DELETE FROM employee;       -- Wipes the entire table clean
```

### 🔹 Delete a Specific Row

```sql
-- Removes only the employee with emp_id = 12
DELETE FROM employee
WHERE emp_id = 12;
```

---

## 📊 Quick Recap — Command Summary

|Command|Purpose|
|---|---|
|`WHERE col = value`|Filter by exact match|
|`WHERE col > / < value`|Filter by comparison|
|`WHERE c1 AND c2`|Both conditions must be true|
|`WHERE c1 OR c2`|Either condition can be true|
|`WHERE col IN (...)`|Match any value in the list|
|`WHERE col NOT IN (...)`|Exclude values in the list|
|`WHERE col BETWEEN a AND b`|Inclusive range filter|
|`WHERE col LIKE 'pattern'`|Pattern-based search|
|`LIMIT n`|Restrict number of rows returned|
|`UPDATE ... SET ... WHERE`|Modify specific rows|
|`DELETE FROM ... WHERE`|Remove specific rows|

---

> [!success] Exam Ready ⭐
> 
> - `WHERE` → **filters rows** based on condition
> - `%` → **any number** of characters  |  `_` → **exactly one** character
> - Always use `WHERE` with `UPDATE` and `DELETE` to avoid modifying all rows!

---

