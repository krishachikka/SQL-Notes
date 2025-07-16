## SQL Syntax

SQL commands follow a specific structure to interact with the database. The syntax is mostly straightforward and English-like.

### Basic Structure

```sql
SELECT column1, column2 FROM table_name WHERE condition;
```

### Common SQL Keywords

* `SELECT` – fetch data
* `FROM` – specify the table
* `WHERE` – filter rows
* `INSERT INTO` – add new data
* `UPDATE` – modify existing data
* `DELETE` – remove data
* `CREATE` – make new tables/databases
* `DROP` – delete tables/databases
* `ALTER` – modify table structure

### Rules to Remember

* SQL keywords are **not case-sensitive** (`SELECT` = `select`), but uppercase is preferred for readability
* Statements end with a **semicolon (;)**
* Strings are enclosed in **single quotes** (`'value'`)
* Column and table names shouldn’t be in quotes unless they contain spaces or reserved words

---

## SQL Data Types

Data types define the kind of value a column can store. They vary slightly across databases, but the core types are mostly the same.

### 1. Numeric Types

* `INT` – Integer numbers (e.g., 1, 42)
* `FLOAT` / `REAL` – Approximate decimal numbers
* `DECIMAL(p, s)` – Exact decimal numbers with precision (`p`) and scale (`s`)
* `SMALLINT`, `BIGINT` – Smaller or larger integer ranges

### 2. String/Text Types

* `CHAR(n)` – Fixed-length string
* `VARCHAR(n)` – Variable-length string (most commonly used)
* `TEXT` – Large text data (can store paragraphs)

### 3. Date and Time Types

* `DATE` – Stores date only (`YYYY-MM-DD`)
* `TIME` – Stores time only (`HH:MM:SS`)
* `DATETIME` – Stores both date and time
* `TIMESTAMP` – Similar to `DATETIME` but auto-updates with current time (useful for logs)

### 4. Boolean Type

* `BOOLEAN` or `BOOL` – Stores `TRUE` or `FALSE` values

---
[← Introduction](./Intro.md) | [Next → SQL Statements](./Statements.md)