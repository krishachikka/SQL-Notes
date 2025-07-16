# SQL Indexes

An **index** is a data structure that makes data retrieval faster. It works like an index in a book—jumping straight to what you need.

---

## Why Use Indexes?

- Improve query performance, especially on large tables
- Speed up `WHERE`, `ORDER BY`, and `JOIN` operations
- Reduce scan time by allowing the database to “look up” values directly

---

## Basic Syntax: Creating an Index

```sql
CREATE INDEX index_name
ON table_name (column1, column2, ...);
````

### Example

```sql
CREATE INDEX idx_students_age
ON students(age);
```

---

## Composite Index (Multiple Columns)

```sql
CREATE INDEX idx_students_city_age
ON students(city, age);
```

This index works best when queries filter by **city first**, then age.

---

## Unique Index

Prevents duplicate values in a column (similar to `UNIQUE` constraint).

```sql
CREATE UNIQUE INDEX idx_students_email
ON students(email);
```

---

## Dropping an Index

```sql
DROP INDEX idx_students_age;
```

(Note: Syntax may vary—e.g., in MySQL it's: `DROP INDEX idx_name ON table_name;`)

---

## When to Use Indexes

* On columns frequently used in `WHERE`, `JOIN`, or `ORDER BY`
* On foreign keys and primary keys (automatically indexed)
* On columns with high selectivity (many unique values)

---

## When Not to Use Indexes

* On small tables (not much benefit)
* On columns that are rarely queried
* On columns with lots of duplicate values (low selectivity)
* When doing frequent `INSERT`/`UPDATE`—indexes can slow those down

---

## Checking Indexes (Example: MySQL)

```sql
SHOW INDEXES FROM students;
```

---

## TL;DR

| Feature    | Impact                          |
| ---------- | ------------------------------- |
| Speeds up  | SELECT, JOIN, WHERE, ORDER BY   |
| Slows down | INSERT, UPDATE, DELETE          |
| Best for   | Large tables, high-read queries |