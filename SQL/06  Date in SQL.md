# 📅 SQL Date Functions — Complete Reference

> [!NOTE] About This Note A complete guide to working with **DATE** data types in MySQL — covering column creation, formatting, arithmetic, and real query outputs.

---

## 🏗️ Setting Up — Add & Populate a Date Column

### Step 1 · Add the Column

```sql
ALTER TABLE employee ADD COLUMN Hire_Date DATE;
```

> [!TIP] What This Does Adds a new `DATE` column called `Hire_Date` to the existing `employee` table.

**Output — Table Structure After ALTER:**

|emp_id|name|job_desc|Hire_Date|
|---|---|---|---|
|101|Alice|MANAGER|`NULL`|
|102|Bob|ANALYST|`NULL`|
|103|Carol|DEVELOPER|`NULL`|

---

### Step 2 · Set a Default Date for All Rows

```sql
UPDATE employee
SET Hire_Date = "2012-10-05";
```

**Output — After Global Update:**

|emp_id|name|job_desc|Hire_Date|
|---|---|---|---|
|101|Alice|MANAGER|2012-10-05|
|102|Bob|ANALYST|2012-10-05|
|103|Carol|DEVELOPER|2012-10-05|

---

### Step 3 · Override Date for a Specific Group

```sql
UPDATE employee
SET Hire_Date = "2014-10-05"
WHERE job_desc = "ANALYST";
```

**Output — After Conditional Update:**

|emp_id|name|job_desc|Hire_Date|
|---|---|---|---|
|101|Alice|MANAGER|2012-10-05|
|102|Bob|ANALYST|**2014-10-05**|
|103|Carol|DEVELOPER|2012-10-05|

---

## 🕐 Getting the Current Date & Time

### `NOW()` — Current Date + Time

```sql
SELECT NOW();
```

|NOW()|
|---|
|`2025-04-27 14:35:22`|

---

### `DATE(NOW())` — Extract Only the Date Part

```sql
SELECT DATE(NOW());
```

|DATE(NOW())|
|---|
|`2025-04-27`|

> [!INFO] Difference from `NOW()` `DATE(NOW())` strips the time component, returning only `YYYY-MM-DD`.

---

### `CURDATE()` — Shorthand for Current Date

```sql
SELECT CURDATE();
```

|CURDATE()|
|---|
|`2025-04-27`|

> [!TIP] `CURDATE()` ≡ `DATE(NOW())` — both return the same result. Use `CURDATE()` for brevity.

---

## 🎨 Formatting Dates — `DATE_FORMAT()`

```sql
SELECT DATE_FORMAT(CURDATE(), '%d/%m/%Y');
```

|DATE_FORMAT(CURDATE(), '%d/%m/%Y')|
|---|
|`27/04/2025`|

### 📋 Format Specifier Quick Reference

|Specifier|Meaning|Example|
|---|---|---|
|`%d`|Day (01–31)|`27`|
|`%m`|Month (01–12)|`04`|
|`%Y`|Year (4 digits)|`2025`|
|`%y`|Year (2 digits)|`25`|
|`%M`|Month name|`April`|
|`%D`|Day with suffix|`27th`|
|`%W`|Weekday name|`Sunday`|

**More Format Examples:**

```sql
SELECT DATE_FORMAT(CURDATE(), '%W, %D %M %Y');  -- Sunday, 27th April 2025
SELECT DATE_FORMAT(CURDATE(), '%Y-%m-%d');        -- 2025-04-27 (ISO format)
SELECT DATE_FORMAT(CURDATE(), '%d-%b-%Y');        -- 27-Apr-2025
```

---

## 📐 Calculating Date Differences — `DATEDIFF()`

```sql
SELECT DATEDIFF(CURDATE(), '2020-01-01') AS DAYS;
```

|DAYS|
|---|
|`1943`|

> [!INFO] Syntax `DATEDIFF(end_date, start_date)` → Returns **end − start** in **days** (positive if end is later).

**More Examples:**

```sql
-- Days since hire
SELECT name, DATEDIFF(CURDATE(), Hire_Date) AS Days_Employed
FROM employee;
```

|name|Days_Employed|
|---|---|
|Alice|`4586`|
|Bob|`3856`|
|Carol|`4586`|

---

## ➕ Date Arithmetic — `DATE_ADD()`

```sql
SELECT
  CURDATE()                              AS 'Start Date',
  DATE_ADD(CURDATE(), INTERVAL 1 DAY)   AS 'One Day Later',
  DATE_ADD(CURDATE(), INTERVAL 1 WEEK)  AS 'One Week Later',
  DATE_ADD(CURDATE(), INTERVAL 1 MONTH) AS 'One Month Later',
  DATE_ADD(CURDATE(), INTERVAL 1 YEAR)  AS 'One Year Later';
```

> [!WARNING] Typo in Original The original query had a stray `x` after `'one month later',` — removed here for correctness.

**Output:**

|Start Date|One Day Later|One Week Later|One Month Later|One Year Later|
|---|---|---|---|---|
|`2025-04-27`|`2025-04-28`|`2025-05-04`|`2025-05-27`|`2026-04-27`|

### 📋 INTERVAL Units Reference

|Unit|Example|Description|
|---|---|---|
|`DAY`|`INTERVAL 7 DAY`|Adds 7 days|
|`WEEK`|`INTERVAL 2 WEEK`|Adds 2 weeks|
|`MONTH`|`INTERVAL 3 MONTH`|Adds 3 months|
|`YEAR`|`INTERVAL 1 YEAR`|Adds 1 year|
|`HOUR`|`INTERVAL 6 HOUR`|Adds 6 hours|
|`MINUTE`|`INTERVAL 30 MINUTE`|Adds 30 minutes|

> [!TIP] Subtraction Use `DATE_SUB()` or a negative interval to go **back** in time:
> 
> ```sql
> SELECT DATE_SUB(CURDATE(), INTERVAL 30 DAY);  -- 30 days ago
> ```

---

## 🗺️ Summary — Function Cheat Sheet

|Function|Returns|Example Output|
|---|---|---|
|`NOW()`|Date + Time|`2025-04-27 14:35:22`|
|`CURDATE()`|Date only|`2025-04-27`|
|`DATE(NOW())`|Date only|`2025-04-27`|
|`DATE_FORMAT(date, fmt)`|Formatted string|`27/04/2025`|
|`DATEDIFF(d1, d2)`|Integer (days)|`1943`|
|`DATE_ADD(date, INTERVAL n unit)`|New date|`2026-04-27`|
|`DATE_SUB(date, INTERVAL n unit)`|New date|`2024-04-27`|

---

> [!CAUTION] Common Pitfalls
> 
> - Always quote date strings: `'2020-01-01'` ✅ not `2020-01-01` ❌
> - `DATEDIFF` returns **days only** — use `TIMESTAMPDIFF` for hours/minutes
> - Month arithmetic with `DATE_ADD` handles end-of-month edge cases automatically

---
