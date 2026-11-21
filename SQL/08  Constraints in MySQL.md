# 🔒 SQL — Constraints

> [!NOTE] What Are Constraints? Constraints are **rules enforced on columns** to maintain data accuracy, consistency, and integrity. They prevent invalid data from entering the database at the point of insertion or update.

---

## 📋 Constraints at a Glance

|Constraint|Purpose|
|---|---|
|`PRIMARY KEY`|Uniquely identifies each row; combines NOT NULL + UNIQUE|
|`AUTO_INCREMENT`|Automatically generates the next integer value for a column|
|`NOT NULL`|Prevents a column from accepting `NULL` values|
|`DEFAULT`|Assigns a fallback value when no value is provided|
|`UNIQUE`|Ensures all values in the column are distinct|
|`CHECK`|Validates that values satisfy a given condition|

---

## 🏗️ Creating a Table with All Constraints

```sql
CREATE TABLE employee (
    emp_id   INT          PRIMARY KEY AUTO_INCREMENT, -- id will be auto incremented for new rows
    ename    VARCHAR(30)  NOT NULL,                   -- null value cannot be inserted for the column
    job_desc VARCHAR(20)  DEFAULT 'unassigned',        -- sets default when not mentioned
    salary   INT,
    pan      VARCHAR(10)  UNIQUE,                     -- cannot contain duplicates
    CHECK (salary > 100000)                           -- salary must be greater than 1,00,000
);
```

---

## 🔍 Constraint Deep Dive

### 1️⃣ PRIMARY KEY + AUTO_INCREMENT

```sql
emp_id INT PRIMARY KEY AUTO_INCREMENT
```

> [!INFO] How It Works
> 
> - `PRIMARY KEY` = `NOT NULL` + `UNIQUE` combined — every row **must** have a unique, non-null ID
> - `AUTO_INCREMENT` automatically assigns the **next available integer** when a new row is inserted
> - You **never need to manually provide** `emp_id` — MySQL handles it

**Behaviour:**

|Action|emp_id assigned|
|---|---|
|First INSERT|`1`|
|Second INSERT|`2`|
|Third INSERT|`3`|
|(even after a DELETE)|continues from last max value|

---

### 2️⃣ NOT NULL

```sql
ename VARCHAR(30) NOT NULL
```

> [!Info] How It Works
> 
> - The column **refuses** any `INSERT` or `UPDATE` that doesn't provide a value
> - Without `NOT NULL`, omitting a column automatically stores `NULL`

**Allowed vs Rejected:**

|Statement|Result|
|---|---|
|`INSERT INTO employee(ename, salary) VALUES ('Ramya', 1000000)`|✅ Allowed|
|`INSERT INTO employee(salary) VALUES (1000000)`|❌ Error — `ename` cannot be null|

---

### 3️⃣ DEFAULT

```sql
job_desc VARCHAR(20) DEFAULT 'unassigned'
```

> [!Info] How It Works
> 
> - When `job_desc` is **not mentioned** in the INSERT statement, MySQL automatically stores `'unassigned'`
> - The default kicks in **only when the column is omitted** — if you explicitly pass `NULL`, it stores `NULL`

**Behaviour:**

|INSERT includes `job_desc`?|Value stored|
|---|---|
|No (omitted)|`'unassigned'`|
|Yes → `'ANALYST'`|`'ANALYST'`|
|Yes → `NULL`|`NULL`|

---

### 4️⃣ UNIQUE

```sql
pan VARCHAR(10) UNIQUE
```

> [!Info] How It Works
> 
> - No two rows can have the **same PAN value**
> - Unlike `PRIMARY KEY`, a `UNIQUE` column **can hold `NULL`** (and multiple rows can be `NULL`)
> - Ideal for fields like PAN, Aadhaar, Email, Phone — which must be one-per-person

**Allowed vs Rejected:**

|emp_id|pan|Result|
|---|---|---|
|1|`ABCDE1234F`|✅ Inserted|
|2|`XYZPQ9876G`|✅ Inserted|
|3|`ABCDE1234F`|❌ Error — Duplicate entry|
|4|`NULL`|✅ Allowed (NULL ≠ a value)|

---

### 5️⃣ CHECK

```sql
CHECK (salary > 100000)
```

> [!Info] How It Works
> 
> - MySQL evaluates the condition **every time a row is inserted or updated**
> - If the condition is `FALSE`, the operation is **rejected with an error**
> - Supports any valid boolean expression: `>`, `<`, `=`, `BETWEEN`, `IN`, `LIKE`, etc.

**Allowed vs Rejected:**

|salary inserted|Condition `salary > 100000`|Result|
|---|---|---|
|`1000000`|✅ TRUE|Row accepted|
|`10000`|❌ FALSE|Error — CHECK constraint failed|
|`100001`|✅ TRUE|Row accepted|
|`100000`|❌ FALSE (not strictly >)|Error — must be **greater than**|

---

## 📝 INSERT Statements & Outputs

### ✅ Valid Insert — Ramya

```sql
INSERT INTO employee(ename, salary) VALUES ('Ramya', 1000000);
```

> [!TIP] What Happens
> 
> - `emp_id` → auto-assigned as `1`
> - `ename` → `'Ramya'` ✅ (NOT NULL satisfied)
> - `job_desc` → `'unassigned'` ✅ (DEFAULT applied — column was omitted)
> - `salary` → `1000000` ✅ (CHECK passes: 1000000 > 100000)
> - `pan` → `NULL` ✅ (UNIQUE allows NULL)

**Result after INSERT:**

|emp_id|ename|job_desc|salary|pan|
|---|---|---|---|---|
|1|Ramya|unassigned|1,000,000|NULL|

---

### ❌ Invalid Insert — Riya

```sql
INSERT INTO employee(ename, salary) VALUES ('Riya', 10000);
```

> [!CAUTION] Why This Fails
> 
> - `salary = 10000` → CHECK condition `salary > 100000` evaluates to **FALSE**
> - MySQL **rejects the entire row** — nothing is inserted
> - Error message: `ERROR 3819 (HY000): Check constraint 'employee_chk_1' is violated.`

**Result — Table unchanged:**

|emp_id|ename|job_desc|salary|pan|
|---|---|---|---|---|
|1|Ramya|unassigned|1,000,000|NULL|

---

## 🔎 SELECT — View Final Table

```sql
SELECT * FROM employee;
```

**Output:**

|emp_id|ename|job_desc|salary|pan|
|---|---|---|---|---|
|1|Ramya|unassigned|1,000,000|NULL|

> [!INFO] Observation Only **one row** exists because Riya's insert was blocked by the `CHECK` constraint on salary. `emp_id = 1` was auto-generated, and `job_desc = 'unassigned'` was filled by the `DEFAULT`.

---

## ⚠️ Common Constraint Errors

|Scenario|Error Type|Constraint Violated|
|---|---|---|
|Inserting duplicate PAN|`Duplicate entry`|`UNIQUE`|
|Omitting `ename`|`Field doesn't have a default`|`NOT NULL`|
|`salary = 50000`|`Check constraint is violated`|`CHECK`|
|Manually inserting a duplicate `emp_id`|`Duplicate entry for PRIMARY KEY`|`PRIMARY KEY`|

---

## 🗺️ Constraint Summary

```
┌─────────────────────────────────────────────────────────────┐
│                     employee TABLE                          │
│                                                             │
│  emp_id  ──── PRIMARY KEY + AUTO_INCREMENT                  │
│               └─ Unique, Not Null, Auto-assigned            │
│                                                             │
│  ename   ──── NOT NULL                                      │
│               └─ Must always have a value                   │
│                                                             │
│  job_desc ─── DEFAULT 'unassigned'                          │
│               └─ Falls back when omitted                    │
│                                                             │
│  salary  ──── CHECK (salary > 100000)                       │
│               └─ Rejected if condition is false             │
│                                                             │
│  pan     ──── UNIQUE                                        │
│               └─ No duplicates; NULLs allowed               │
└─────────────────────────────────────────────────────────────┘
```

---

