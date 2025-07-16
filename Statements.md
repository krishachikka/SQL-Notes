## SQL Constraints

Constraints are rules applied to table columns to enforce data integrity. They make sure the data stays valid and reliable.

### Common Constraints:

### 1. `NOT NULL`

* Ensures a column can't have `NULL` (empty) values

```sql
name VARCHAR(100) NOT NULL
```

### 2. `UNIQUE`

* Ensures all values in a column are different

```sql
email VARCHAR(100) UNIQUE
```

### 3. `PRIMARY KEY`

* Uniquely identifies each row in a table
* Combines `NOT NULL` + `UNIQUE`

```sql
id INT PRIMARY KEY
```

### 4. `FOREIGN KEY`

* Creates a link between two tables
* Enforces referential integrity

```sql
FOREIGN KEY (user_id) REFERENCES users(id)
```

### 5. `CHECK`

* Limits the values that can be stored in a column

```sql
age INT CHECK (age >= 18)
```

### 6. `DEFAULT`

* Sets a default value if none is provided

```sql
status VARCHAR(20) DEFAULT 'active'
```
---

## `SELECT` Statement

The `SELECT` statement is used to **retrieve data** from a table.

### Basic Syntax:

```sql
SELECT column1, column2 FROM table_name;
```

### Example:

```sql
SELECT name, age FROM students;
```

### Select All Columns:

```sql
SELECT * FROM students;
```

### Use of `WHERE` Clause:

Filters rows based on a condition.

```sql
SELECT * FROM students WHERE age > 18;
```

### `DISTINCT` Keyword:

Removes duplicate values.

```sql
SELECT DISTINCT city FROM students;
```

### Sorting Results - `ORDER BY`:

```sql
SELECT name, age FROM students ORDER BY age DESC;
```

### Limiting Rows - `LIMIT`:

```sql
SELECT * FROM students LIMIT 5;
```

---

## `INSERT INTO` Statement

Used to **add new records** (rows) into a table.

### Basic Syntax:

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

### Example:

```sql
INSERT INTO students (name, age, city)
VALUES ('Krisha', 20, 'Mumbai');
```

### Inserting into All Columns:

Only works if you’re providing values for **every column**, in correct order.

```sql
INSERT INTO students
VALUES (101, 'Krisha', 20, 'Mumbai');
```

### Insert Multiple Rows:

```sql
INSERT INTO students (name, age, city)
VALUES 
  ('Tanu', 21, 'Delhi'),
  ('Dev', 22, 'Pune');
```
---

## `UPDATE` Statement

Used to **modify existing records** in a table.

### Syntax:

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

### Example:

```sql
UPDATE students
SET age = 20
WHERE name = 'Aarav';
```

**Important:** Always use a `WHERE` clause—without it, *every* row in the table will be updated.

---

## `DELETE` Statement

Used to **remove records** from a table.

### Syntax:

```sql
DELETE FROM table_name
WHERE condition;
```

### Example:

```sql
DELETE FROM students
WHERE age < 18;
```

Same warning here—no `WHERE` clause means **everything** gets deleted.

---
[← SQL Syntax](./Syntax.md) | [Next → Tables](./table.md)