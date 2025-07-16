# SQL Joins

Joins are used to combine rows from two or more tables based on a related column between them.

---

## Example Tables

**students**
| id | name  |
|----|-------|
| 1  | Ayaan |
| 2  | Riya  |

**enrollments**
| student_id | course_name |
|------------|-------------|
| 1          | Math        |
| 1          | Physics     |
| 2          | Chemistry   |

---

## 1. INNER JOIN

Returns rows where there is a match in **both** tables.

```sql
SELECT students.name, enrollments.course_name
FROM students
INNER JOIN enrollments
ON students.id = enrollments.student_id;
````

---

## 2. LEFT JOIN (or LEFT OUTER JOIN)

Returns all rows from the **left** table, and matched rows from the right table.

```sql
SELECT students.name, enrollments.course_name
FROM students
LEFT JOIN enrollments
ON students.id = enrollments.student_id;
```

If there's no match, `course_name` will be `NULL`.

---

## 3. RIGHT JOIN (or RIGHT OUTER JOIN)

Returns all rows from the **right** table, and matched rows from the left.

```sql
SELECT students.name, enrollments.course_name
FROM students
RIGHT JOIN enrollments
ON students.id = enrollments.student_id;
```

---

## 4. FULL JOIN (or FULL OUTER JOIN)

Returns all rows when there is a match in **either** table.

```sql
SELECT students.name, enrollments.course_name
FROM students
FULL JOIN enrollments
ON students.id = enrollments.student_id;
```

Not supported in all DBMSs (e.g., MySQL needs workaround).

---

## 5. CROSS JOIN

Returns the **cartesian product**—every row of one table with every row of the other.

```sql
SELECT students.name, enrollments.course_name
FROM students
CROSS JOIN enrollments;
```

---

## Join Summary

| Type       | What it does                         |
| ---------- | ------------------------------------ |
| INNER JOIN | Matches in both tables only          |
| LEFT JOIN  | All from left, matched from right    |
| RIGHT JOIN | All from right, matched from left    |
| FULL JOIN  | All from both, matched and unmatched |
| CROSS JOIN | All combinations (cartesian product) |

---
[← Clauses](./clauses.md) | [Next → Aggregate Functions](./aggregate.md)