# SQL Clauses

Clauses are used in SQL to filter, sort, group, and control query output. They are often combined with `SELECT` statements.

---

## 1. WHERE

Filters rows based on a condition.

```sql
SELECT * FROM students
WHERE age >= 18;
````

Supports logical operators: `AND`, `OR`, `NOT`, comparison operators: `=`, `!=`, `<`, `>`, `BETWEEN`, `LIKE`, `IN`

---

## 2. ORDER BY

Sorts the result in ascending (default) or descending order.

```sql
SELECT name, age FROM students
ORDER BY age DESC;
```

---

## 3. GROUP BY

Groups rows with the same value in specified column(s). Often used with aggregate functions.

```sql
SELECT city, COUNT(*) FROM students
GROUP BY city;
```

---

## 4. HAVING

Filters grouped data. Used **after** `GROUP BY`.

```sql
SELECT city, COUNT(*) FROM students
GROUP BY city
HAVING COUNT(*) > 2;
```

---

## 5. LIMIT / TOP / FETCH

Used to restrict the number of rows returned.

### MySQL / PostgreSQL

```sql
SELECT * FROM students
LIMIT 5;
```

### SQL Server

```sql
SELECT TOP 5 * FROM students;
```

---

## Notes

* `WHERE` filters **before** grouping
* `HAVING` filters **after** grouping
* `ORDER BY` always comes **last**

---

## Clause Order in a Query (Standard Flow)

```sql
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
```

Perfect question. SQL wildcards (`LIKE`, `%`, `_`, etc.) deserve their own spotlight but also belong where users learn about filtering.

---

## SQL Wildcards (with LIKE)

Wildcards are special characters used with the `LIKE` operator in the `WHERE` clause to search for patterns in text.

### Common Wildcards

| Symbol | Description                                | Example Match                     |
|--------|--------------------------------------------|-----------------------------------|
| `%`    | Matches any sequence of characters         | `'A%'` → matches "Alice", "Aarav" |
| `_`    | Matches any single character               | `'A_a'` → matches "Ana", "Aba"    |
| `[abc]`| Matches any one character inside brackets   | `'R[ae]m'` → matches "Ram", "Rem" |
| `[^abc]`| Matches any one character *not* listed     | `'K[^ae]n'` → matches "Kin", not "Ken" |
| `[a-z]`| Matches any character in the range          | `'S[a-z]m'` → matches "Sam", "Sim"|

> Note: Some wildcard patterns like `[]` and `[^]` are only supported in certain databases like SQL Server. Stick to `%` and `_` for cross-platform usage.

### Examples

```sql
-- Names that start with 'A'
SELECT * FROM Student WHERE Name LIKE 'A%';

-- Names that end with 'n'
SELECT * FROM Student WHERE Name LIKE '%n';

-- Names with 'a' as second character
SELECT * FROM Student WHERE Name LIKE '_a%';

-- Names exactly 4 characters long
SELECT * FROM Student WHERE Name LIKE '____';
```

Use `NOT LIKE` to exclude patterns:

```sql
-- Names that don't start with 'K'
SELECT * FROM Student WHERE Name NOT LIKE 'K%';
```

---
[← Tables](./table.md) | [Next → Joins](./joins.md)
