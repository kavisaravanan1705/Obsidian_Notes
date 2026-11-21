
# 🔑 Foreign Key

> [!info] Definition A **Foreign Key** is a field (or collection of fields) in one table that refers to the **Primary Key** of another table. It is used to establish and enforce a **link between data in two tables**, ensuring **referential integrity**.

---

## 📌 Key Concepts

- The table containing the foreign key is called the **child table** (or referencing table).
- The table being referred to is called the **parent table** (or referenced table).
- The foreign key value in the child table **must match** an existing primary key in the parent table — or be `NULL`.

---

## 🏗️ Example 1: Creating Tables with a Foreign Key

```sql
-- Step 1: Create the parent table (branch)
CREATE TABLE branch (
    branch_id INT PRIMARY KEY AUTO_INCREMENT,
    br_name   VARCHAR(30) NOT NULL,
    addr      VARCHAR(200)
);

-- Step 2: Create the child table (employee) with branch_id as a foreign key
--         branch_id here references branch_id in the branch table
CREATE TABLE employee (
    emp_id    INT PRIMARY KEY,
    ename     VARCHAR(30),
    job_desc  VARCHAR(20),
    salary    INT,
    branch_id INT,
    CONSTRAINT FK_branchId
        FOREIGN KEY (branch_id)
        REFERENCES branch(branch_id)
);
```

> [!tip] What's happening?
> 
> - `branch` is the **parent** table. Its `branch_id` is the **Primary Key**.
> - `employee` is the **child** table. Its `branch_id` is the **Foreign Key** pointing to `branch.branch_id`.
> - `CONSTRAINT FK_branchId` gives the foreign key a named constraint for easier management.

---

## 📥 Example 2: Inserting Data (Respecting FK Rules)

```sql
-- Insert into parent table first
INSERT INTO branch (br_name, addr) VALUES ('Head Office', '123 Main St');
INSERT INTO branch (br_name, addr) VALUES ('South Branch', '456 Park Ave');

-- Now insert into child table using valid branch_id values
INSERT INTO employee VALUES (1, 'Alice',  'Manager',  75000, 1);
INSERT INTO employee VALUES (2, 'Bob',    'Analyst',  55000, 2);
INSERT INTO employee VALUES (3, 'Charlie','Developer',60000, 1);

-- ❌ This will FAIL — branch_id 99 does not exist in branch table
INSERT INTO employee VALUES (4, 'Dave', 'Intern', 30000, 99);
-- ERROR: Cannot add or update a child row: a foreign key constraint fails
```

---

## 🚫 Example 3: Attempting to Delete a Parent Row (FK Violation)

```sql
-- ❌ This will FAIL if employees still reference branch_id = 1
DELETE FROM branch WHERE branch_id = 1;
-- ERROR: Cannot delete or update a parent row: a foreign key constraint fails

-- ✅ First delete or update child rows, then delete parent
DELETE FROM employee WHERE branch_id = 1;
DELETE FROM branch  WHERE branch_id = 1;
```

---

## 🔄 Example 4: ON DELETE and ON UPDATE Cascade Actions

```sql
-- Recreate employee table with CASCADE options
CREATE TABLE employee (
    emp_id    INT PRIMARY KEY,
    ename     VARCHAR(30),
    job_desc  VARCHAR(20),
    salary    INT,
    branch_id INT,
    CONSTRAINT FK_branchId
        FOREIGN KEY (branch_id)
        REFERENCES branch(branch_id)
        ON DELETE CASCADE      -- Auto-delete child rows when parent is deleted
        ON UPDATE CASCADE      -- Auto-update FK value when parent PK changes
);

-- Now deleting a branch automatically deletes its employees
DELETE FROM branch WHERE branch_id = 1;
-- All employees with branch_id = 1 are automatically deleted ✅
```

### Available Referential Actions

|Action|Description|
|---|---|
|`CASCADE`|Automatically delete/update child rows|
|`SET NULL`|Set FK column to `NULL` when parent is deleted/updated|
|`SET DEFAULT`|Set FK column to its default value|
|`RESTRICT`|Prevent deletion/update if child rows exist (default)|
|`NO ACTION`|Similar to RESTRICT; checked at end of transaction|

---

## ➕ Example 5: Adding a Foreign Key to an Existing Table (ALTER TABLE)

```sql
-- Suppose employee table already exists WITHOUT the foreign key
-- Add a foreign key constraint using ALTER TABLE

ALTER TABLE employee
ADD CONSTRAINT FK_branchId
    FOREIGN KEY (branch_id)
    REFERENCES branch(branch_id);
```

---

## ➖ Example 6: Dropping a Foreign Key Constraint

```sql
-- Drop the named foreign key constraint from employee table
ALTER TABLE employee
DROP FOREIGN KEY FK_branchId;
```

> [!warning] Note After dropping the FK, the `branch_id` column still exists in the table — only the **constraint** (the enforcement rule) is removed. The column becomes a plain `INT` with no referential integrity enforced.

---

## 🔍 Example 7: Checking Existing Foreign Keys

```sql
-- View all foreign key constraints in the current database
SELECT
    TABLE_NAME,
    COLUMN_NAME,
    CONSTRAINT_NAME,
    REFERENCED_TABLE_NAME,
    REFERENCED_COLUMN_NAME
FROM
    INFORMATION_SCHEMA.KEY_COLUMN_USAGE
WHERE
    REFERENCED_TABLE_SCHEMA = 'your_database_name'
    AND REFERENCED_TABLE_NAME IS NOT NULL;
```

---

## 🌐 Example 8: Multi-Column Foreign Key

```sql
-- Parent table with composite primary key
CREATE TABLE department (
    dept_id   INT,
    dept_code VARCHAR(10),
    dept_name VARCHAR(50),
    PRIMARY KEY (dept_id, dept_code)
);

-- Child table referencing both columns as a composite FK
CREATE TABLE staff (
    staff_id  INT PRIMARY KEY,
    sname     VARCHAR(30),
    dept_id   INT,
    dept_code VARCHAR(10),
    CONSTRAINT FK_dept
        FOREIGN KEY (dept_id, dept_code)
        REFERENCES department(dept_id, dept_code)
);
```

---

## 🧠 Summary

|Feature|Details|
|---|---|
|Purpose|Enforce referential integrity between two tables|
|Defined in|Child (referencing) table|
|Points to|Primary Key of parent (referenced) table|
|Named Constraint|`CONSTRAINT <name> FOREIGN KEY`|
|Add later|`ALTER TABLE ... ADD CONSTRAINT ... FOREIGN KEY`|
|Remove|`ALTER TABLE ... DROP FOREIGN KEY <name>`|
|Cascade options|`CASCADE`, `SET NULL`, `SET DEFAULT`, `RESTRICT`|
|Violation result|Error — operation is rejected by the DBMS|

---
