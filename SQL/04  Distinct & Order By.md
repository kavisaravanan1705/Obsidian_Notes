# 🔀 DISTINCT & ORDER BY

---

## 🧹 DISTINCT — Remove Duplicates

> [!abstract] What is DISTINCT? `DISTINCT` returns only **unique values** from a column — duplicate entries are automatically removed from the result.

### 📐 Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

### 🔹 Example

```sql
-- Shows only unique job roles (no duplicates)
SELECT DISTINCT job_desc
FROM employee;
```

> [!example] Output Idea Instead of seeing `MANAGER` appear 3 times, `DISTINCT` shows it **only once**.

---

## 📶 ORDER BY — Sort Results

> [!abstract] What is ORDER BY? `ORDER BY` is used to **sort** the result set in either **ascending** or **descending** order.
> 
> |Keyword|Behaviour|
> |---|---|
> |`ASC`|Ascending order _(default — smallest to largest)_|
> |`DESC`|Descending order _(largest to smallest)_|

> [!tip] Default Behaviour If you don't specify `ASC` or `DESC`, SQL sorts in **ascending order by default**.

---

## 🧪 ORDER BY — Query Examples

### 🔹 Sort by Salary — Ascending (Default)

```sql
-- Sorts all employees by salary from lowest to highest
SELECT * FROM employee
ORDER BY salary;
```

### 🔹 Sort by Salary — Explicit ASC

```sql
-- Same as above, but explicitly stated
SELECT * FROM employee
ORDER BY salary ASC;
```

### 🔹 Sort by Salary — Descending

```sql
-- Sorts all employees by salary from highest to lowest
SELECT * FROM employee
ORDER BY salary DESC;
```

### 🔹 Filter + Sort Together

```sql
-- Shows only MANAGERs, sorted by salary from highest to lowest
SELECT * FROM employee
WHERE job_desc = "MANAGER"
ORDER BY salary DESC;
```

### 🔹 Sort by Multiple Columns

```sql
-- First sorts by job_desc alphabetically,
-- then within each job group, sorts by ename alphabetically
SELECT * FROM employee
ORDER BY job_desc, ename;
```

> [!info] How Multi-Column Sorting Works SQL sorts by the **first column** you specify. When there are **ties**, it sorts by the **second column**, and so on.

### 🔹 Custom Sort Order — CASE Inside ORDER BY

```sql
-- Defines a custom priority order for job roles
SELECT * FROM employee
ORDER BY (
    CASE job_desc
        WHEN 'CEO'     THEN 1
        WHEN 'MANAGER' THEN 2
        WHEN 'HR'      THEN 3
        WHEN 'ANALYST' THEN 4
        WHEN 'SALES'   THEN 5
        ELSE 100             -- All other roles go to the bottom
    END
);
```

> [!note] Why Use CASE in ORDER BY? Normal `ORDER BY` sorts **alphabetically or numerically**. `CASE` lets you define your **own custom ranking logic** — perfect for role-based or priority-based ordering.

---

## 📊 Quick Recap — ORDER BY Variations

|Query Pattern|What It Does|
|---|---|
|`ORDER BY col`|Sort ascending _(default)_|
|`ORDER BY col ASC`|Sort ascending _(explicit)_|
|`ORDER BY col DESC`|Sort descending|
|`WHERE ... ORDER BY col DESC`|Filter first, then sort|
|`ORDER BY col1, col2`|Sort by col1, break ties with col2|
|`ORDER BY CASE WHEN ... END`|Custom user-defined sort order|

---

> [!success] Exam Ready ⭐
> 
> - `DISTINCT` → Removes **duplicate** rows from result
> - `ORDER BY` → Sorts results | Default is **ASC**
> - **Multiple columns** → sorted left to right in priority
> - **CASE in ORDER BY** → Define your own **custom sort order**

---

