# 📘 Basic SQL Queries

> [!tip] Quick Note SQL keywords are **case-insensitive**, but writing them in **UPPERCASE** is the standard convention for readability.

---

## 🗄️ Database Queries

> [!info] Commands to create, view, delete, and switch databases

```sql
CREATE DATABASE LOGICFIRST;       -- ✅ Creates a new database

-- ❌ Delete a Database
DROP DATABASE LOGICFIRST;

DROP SCHEMA LOGICFIRST;           -- Same as above (DATABASE = SCHEMA)

DROP SCHEMA IF EXISTS LOGICFIRST; -- 🛡️ Prevents error if DB doesn't exist

-- 👀 View Databases
SHOW DATABASES;                   -- Shows all databases
SHOW SCHEMAS;                     -- Same as above

-- 🔀 Switch Database
USE SYS;                          -- Use this DB for all further commands

-- 📋 View Tables
SHOW TABLES;                      -- Shows all tables in the current database
```

---

## 🏗️ Table — Create, Delete, Alter

> [!note] Primary Key 🔑 **Primary Key** → Uniquely identifies **each row** in a table. No duplicates, no NULLs.

### ✅ Creating a Table

```sql
-- Method 1: Inline Primary Key
CREATE TABLE student (
    id    INT PRIMARY KEY,
    name  VARCHAR(30),
    gpa   DECIMAL(3,2)
);

-- -------- OR --------

-- Method 2: Primary Key at the end
CREATE TABLE student (
    id    INT,
    name  VARCHAR(30),
    gpa   DECIMAL(3,2),
    PRIMARY KEY(id)
);
```

### ❌ Dropping a Table

```sql
DROP TABLE student;    -- Permanently deletes the table
```

### 🔍 Describe a Table

```sql
DESCRIBE student;      -- Shows all columns, types & constraints
```

### ✏️ Altering a Table

```sql
-- ➕ Add a new column
ALTER TABLE student ADD department VARCHAR(5);

-- ➖ Remove a column
ALTER TABLE student DROP COLUMN department;

-- ------- OR -------
ALTER TABLE student DROP department;          -- Same as above
```

---

## 📥 Inserting Data

> [!info] Insert rows into your table using `INSERT INTO`

```sql
-- ✅ Insert a single row (values in column order)
INSERT INTO student VALUES (1, "Aarthi", 7.6);
INSERT INTO student VALUES (2, "Anitha", 8.5);

-- ✅ Insert multiple rows at once
INSERT INTO student VALUES
    (3, "Anitha", 8.5),
    (4, "Arul",   8.2),
    (5, "Ashwin", 7.6);

-- ✅ Insert specific columns only (others will be NULL)
INSERT INTO student (id, name) VALUES
    (5, "Balaji"),
    (6, "Chandru");
```

> [!warning] Column Order Matters! When inserting **all** columns, values must match the exact column order defined in the table.

---

## 🔍 SELECT — Retrieving Data

> [!info] Use `SELECT` to fetch data from your table

```sql
-- 🌐 Select ALL rows and columns
SELECT * FROM student;

-- 🎯 Select SPECIFIC columns only
SELECT id, name FROM student;
```

---

## 📊 Quick Reference Cheat Sheet

| Command             | Purpose                   |
| ------------------- | ------------------------- |
| `CREATE DATABASE`   | Create a new database     |
| `DROP DATABASE`     | Delete a database         |
| `USE`               | Switch to a database      |
| `SHOW DATABASES`    | List all databases        |
| `SHOW TABLES`       | List all tables           |
| `CREATE TABLE`      | Create a new table        |
| `DROP TABLE`        | Delete a table            |
| `DESCRIBE`          | View table structure      |
| `ALTER TABLE ADD`   | Add a new column          |
| `ALTER TABLE DROP`  | Remove a column           |
| `INSERT INTO`       | Add rows to a table       |
| `SELECT *`          | Retrieve all data         |
| `SELECT col1, col2` | Retrieve specific columns |

---

## 🧠 Data Types Used

|Type|Example|Description|
|---|---|---|
|`INT`|`1`, `2`, `100`|Whole numbers|
|`VARCHAR(n)`|`"Aarthi"`|Variable-length string up to n chars|
|`DECIMAL(p,s)`|`7.60`|Decimal number (p = total digits, s = decimal places)|

---

> [!example] Exam Ready ⭐ **`CREATE`** → Make it | **`DROP`** → Delete it | **`ALTER`** → Modify it | **`INSERT`** → Fill it | **`SELECT`** → Read it

---

