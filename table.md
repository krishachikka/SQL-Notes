# Creating Tables in SQL

To store data in a relational database, we first need to create tables.

## Basic Syntax

```sql
CREATE TABLE table_name (
  column1 datatype constraint,
  column2 datatype constraint,
  ...
);
````

## Example

```sql
CREATE TABLE students (
  id INT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  age INT CHECK (age >= 0),
  city VARCHAR(50),
  enrolled_on DATE DEFAULT CURRENT_DATE
);
```

## Key Points

* **Table Name:** Should be meaningful and lowercase (by convention)
* **Columns:** Each column has a name, data type, and optional constraints
* **Semicolon:** Ends the statement

## Common Table-Level Constraints

* `PRIMARY KEY (column)`
* `FOREIGN KEY (column) REFERENCES other_table(column)`
* `UNIQUE (column)`
* `CHECK (condition)`

## Example with Foreign Key

```sql
CREATE TABLE courses (
  course_id INT PRIMARY KEY,
  course_name VARCHAR(100) NOT NULL
);

CREATE TABLE enrollments (
  student_id INT,
  course_id INT,
  enroll_date DATE,
  PRIMARY KEY (student_id, course_id),
  FOREIGN KEY (student_id) REFERENCES students(id),
  FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

## Notes

* Foreign keys enforce relationships between tables.
* Composite primary keys (like in `enrollments`) can be used when one column alone isn't unique.
* Use consistent data types when linking tables.
---

# Modifying and Deleting Tables in SQL

Once a table is created, you can modify or delete it using the following commands:

---

## 1. ALTER TABLE

Used to **change the structure** of an existing table.

### Add a New Column
```sql
ALTER TABLE students
ADD email VARCHAR(100);
````

### Modify an Existing Column

```sql
ALTER TABLE students
MODIFY age INT NOT NULL;
```

### Rename a Column (syntax may vary)

```sql
ALTER TABLE students
RENAME COLUMN city TO hometown;
```

### Drop a Column

```sql
ALTER TABLE students
DROP COLUMN email;
```

---

## 2. DROP TABLE

Used to **permanently delete** the entire table and all its data.

```sql
DROP TABLE students;
```

> Warning: This action is irreversible. The table and its data are gone for good.

---

## 3. TRUNCATE TABLE

Used to **delete all rows** from a table, but keep the structure intact.

```sql
TRUNCATE TABLE students;
```

> Faster than `DELETE` without `WHERE`, but cannot be rolled back in most databases.

---

## Summary

| Command  | What it does                | Reversible? |
| -------- | --------------------------- | ----------- |
| ALTER    | Modify table structure      | Yes         |
| DROP     | Delete table and data       | No          |
| TRUNCATE | Delete all rows, keep table | Usually No  |

```