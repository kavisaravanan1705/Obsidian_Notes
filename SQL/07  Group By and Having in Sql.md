# 🗂️ SQL — GROUP BY & HAVING

> [!NOTE] Core Concept **GROUP BY** groups table rows by a column and lets you analyze each group using **aggregate functions**.
> 
> - **WHERE** → filters **rows** _before_ grouping
> - **HAVING** → filters **groups** _after_ grouping

---

## 📦 Sample Data — `employee` Table

|emp_id|name|job_desc|salary|
|---|---|---|---|
|101|Alice|MANAGER|2,500,000|
|102|Bob|ANALYST|1,200,000|
|103|Carol|ANALYST|1,800,000|
|104|Dave|DEVELOPER|1,600,000|
|105|Eve|DEVELOPER|1,400,000|
|106|Frank|MANAGER|2,200,000|
|107|Grace|DEVELOPER|900,000|

---

## 1️⃣ Average Salary per Job Category

```sql
SELECT job_desc, FORMAT(AVG(salary), 0) avg_sal
FROM employee
GROUP BY job_desc;
```

> [!INFO] What Happens Here
> 
> - Rows are **grouped** by `job_desc`
> - `AVG(salary)` computes the mean salary **within each group**
> - `FORMAT(..., 0)` formats the number with **comma separators**, **0 decimal places**

**Output:**

|job_desc|avg_sal|
|---|---|
|MANAGER|2,350,000|
|ANALYST|1,500,000|
|DEVELOPER|1,300,000|

> [!TIP] `FORMAT()` vs `ROUND()` `FORMAT(value, decimals)` returns a **formatted string** with commas (e.g., `1,500,000`). `ROUND(value, decimals)` returns a **numeric value** — use it when you need to do further math on the result.

---

## 2️⃣ Employee Count per Job Category

```sql
SELECT job_desc, COUNT(emp_id) count
FROM employee
GROUP BY job_desc;
```

> [!INFO] What Happens Here
> 
> - `COUNT(emp_id)` counts the **number of rows** in each group
> - Useful for headcount reports by department or role

**Output:**

|job_desc|count|
|---|---|
|MANAGER|2|
|ANALYST|2|
|DEVELOPER|3|

---

## 3️⃣ HAVING — Filter Groups After Grouping

```sql
SELECT job_desc, COUNT(emp_id) AS count
FROM employee
GROUP BY job_desc
HAVING COUNT(emp_id) > 1;
```

> [!INFO] What Happens Here
> 
> - Groups are formed first by `job_desc`
> - `HAVING COUNT(emp_id) > 1` **removes groups** where only 1 (or 0) employees exist
> - `AS count` is an **alias** — renames the column in output

> [!WARNING] WHERE vs HAVING You **cannot** use `WHERE COUNT(emp_id) > 1` — aggregate functions are not allowed in `WHERE`. Always use **HAVING** to filter on aggregated results.

**Output:**

|job_desc|count|
|---|---|
|MANAGER|2|
|ANALYST|2|
|DEVELOPER|3|

---

## 4️⃣ HAVING + ORDER BY ASC — Alphabetical Sort

```sql
SELECT job_desc, COUNT(emp_id) AS count
FROM employee
GROUP BY job_desc
HAVING COUNT(emp_id) > 1
ORDER BY job_desc;
```

> [!INFO] What Happens Here
> 
> - Same filter as above (`count > 1`)
> - `ORDER BY job_desc` sorts the **result alphabetically** (A → Z) by job description
> - Default sort direction is **ASC** (ascending)

**Output:**

|job_desc|count|
|---|---|
|ANALYST|2|
|DEVELOPER|3|
|MANAGER|2|

---

## 5️⃣ HAVING + ORDER BY DESC — Sort by Group Size

```sql
SELECT job_desc, COUNT(emp_id) AS count
FROM employee
GROUP BY job_desc
HAVING COUNT(emp_id) > 1
ORDER BY COUNT(emp_id) DESC;
```

> [!INFO] What Happens Here
> 
> - Groups are filtered as before
> - `ORDER BY COUNT(emp_id) DESC` sorts groups by **employee count** from **highest → lowest**
> - Useful to quickly spot the largest teams

**Output:**

|job_desc|count|
|---|---|
|DEVELOPER|3|
|ANALYST|2|
|MANAGER|2|

---

## 6️⃣ WHERE + GROUP BY + HAVING + ORDER BY — Full Pipeline

```sql
SELECT job_desc, COUNT(emp_id) AS count
FROM employee
WHERE salary > 1500000
GROUP BY job_desc
HAVING COUNT(emp_id) > 1
ORDER BY COUNT(emp_id) DESC;
```

> [!INFO] What Happens Here — Step by Step
> 
> 1. **WHERE** `salary > 1500000` → filters rows _before_ grouping (only high earners included)
> 2. **GROUP BY** `job_desc` → groups the filtered rows
> 3. **HAVING** `COUNT(emp_id) > 1` → keeps only groups with more than 1 employee
> 4. **ORDER BY** `COUNT(emp_id) DESC` → sorts results by count, highest first

**Rows that survive the WHERE filter (salary > 1,500,000):**

|emp_id|name|job_desc|salary|
|---|---|---|---|
|101|Alice|MANAGER|2,500,000|
|103|Carol|ANALYST|1,800,000|
|104|Dave|DEVELOPER|1,600,000|
|106|Frank|MANAGER|2,200,000|

**After GROUP BY + HAVING (count > 1):**

|job_desc|count|
|---|---|
|MANAGER|2|

> [!CAUTION] Notice `ANALYST` had 2 employees originally, but only **Carol** earns > 1,500,000 — so the ANALYST group has count = 1 and is **excluded** by HAVING. `DEVELOPER` also drops out (only Dave qualifies). Only **MANAGER** survives with 2 qualifying members.

**Final Output:**

|job_desc|count|
|---|---|
|MANAGER|2|

---

## 🗺️ Clause Execution Order — SQL Query Pipeline

```
1. FROM       →  Identify the source table
2. WHERE      →  Filter individual rows (before grouping)
3. GROUP BY   →  Cluster rows into groups
4. HAVING     →  Filter groups (after aggregation)
5. SELECT     →  Choose columns / compute expressions
6. ORDER BY   →  Sort the final result set
```

> [!TIP] Memory Trick **"Furry Wild Geese Have Several Offspring"** **F**ROM → **W**HERE → **G**ROUP BY → **H**AVING → **S**ELECT → **O**RDER BY

---

## 📋 Aggregate Functions Quick Reference

|Function|Description|Example|
|---|---|---|
|`COUNT(col)`|Number of non-NULL rows in group|`COUNT(emp_id)`|
|`SUM(col)`|Total sum within group|`SUM(salary)`|
|`AVG(col)`|Average value within group|`AVG(salary)`|
|`MAX(col)`|Highest value within group|`MAX(salary)`|
|`MIN(col)`|Lowest value within group|`MIN(salary)`|
|`FORMAT(n,d)`|Format number with commas, d decimals|`FORMAT(AVG(salary), 0)`|

---

## 🔑 Summary — WHERE vs HAVING

|Feature|WHERE|HAVING|
|---|---|---|
|Filters|Individual **rows**|**Groups** (after GROUP BY)|
|Runs at stage|Before grouping|After grouping|
|Can use aggregates?|❌ No|✅ Yes|
|Example|`WHERE salary > 1500000`|`HAVING COUNT(emp_id) > 1`|

---

_Tags: #SQL #MySQL #GroupBy #Having #AggregateFunction #Database_