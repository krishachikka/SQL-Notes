# SQL Aggregate Functions

Aggregate functions perform calculations on multiple rows and return a single value. They're often used with `GROUP BY`.

---

## 1. COUNT()

Returns the number of rows.

```sql
SELECT COUNT(*) FROM students;
````

With a condition:

```sql
SELECT COUNT(*) FROM students WHERE age >= 18;
```

---

## 2. SUM()

Returns the total sum of a numeric column.

```sql
SELECT SUM(marks) FROM students;
```

---

## 3. AVG()

Returns the average value of a numeric column.

```sql
SELECT AVG(age) FROM students;
```

---

## 4. MIN() and MAX()

Returns the minimum or maximum value in a column.

```sql
SELECT MIN(age), MAX(age) FROM students;
```

---

## With GROUP BY

Aggregate functions are often paired with `GROUP BY` to summarize grouped data.

```sql
SELECT city, COUNT(*) AS total_students
FROM students
GROUP BY city;
```

---

## Sorting Results (ASC / DESC)

You can sort aggregated results using `ORDER BY`.

```sql
SELECT city, COUNT(*) AS total_students
FROM students
GROUP BY city
ORDER BY total_students DESC;
```

* `ASC` – Sorts in ascending order (default)
* `DESC` – Sorts in descending order

---

## Notes

* Use `AS` to rename result columns (`AS total_students`)
* Can use multiple aggregate functions in one query
* `NULL` values are ignored in calculations (except for `COUNT(*)`)
* Combine `GROUP BY` with `ORDER BY` to control output order
---
[← Joins](./joins.md) | [Next → Subqueries](./subqueries.md)