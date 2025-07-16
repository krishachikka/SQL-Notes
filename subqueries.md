# SQL Subqueries

A **subquery** is a query inside another query. It's used to filter or compute data that depends on other queries.

---

## Types of Subqueries

### 1. In the `WHERE` Clause

Returns values used to filter rows in the outer query.

```sql
SELECT name FROM students
WHERE age > (
  SELECT AVG(age) FROM students
);
````

This returns students older than the average age.

---

### 2. In the `FROM` Clause

Acts like a temporary table (called a derived table).

```sql
SELECT city, avg_age FROM (
  SELECT city, AVG(age) AS avg_age
  FROM students
  GROUP BY city
) AS city_stats
WHERE avg_age > 20;
```

Here, the subquery builds a temp result grouped by city, which the main query filters.

---

### 3. In the `SELECT` Clause

Used for calculated columns per row.

```sql
SELECT name,
  (SELECT COUNT(*) FROM enrollments WHERE enrollments.student_id = students.id) AS total_courses
FROM students;
```

Returns each student’s name with the number of courses they’re enrolled in.

---

## Subquery Categories

### a. Scalar Subquery

Returns **a single value**.

```sql
SELECT name FROM students
WHERE age = (
  SELECT MAX(age) FROM students
);
```

### b. Row Subquery

Returns **multiple columns but only one row**.

```sql
SELECT * FROM employees
WHERE (department, role) = (
  SELECT department, role FROM employees WHERE id = 101
);
```

### c. Table (or Multi-row) Subquery

Returns **multiple rows**.

```sql
SELECT name FROM students
WHERE city IN (
  SELECT city FROM colleges WHERE state = 'Karnataka'
);
```

---

## Correlated Subqueries

This type of subquery depends on the outer query for each row—it runs **once per row**.

```sql
SELECT name FROM students s
WHERE EXISTS (
  SELECT 1 FROM enrollments e
  WHERE e.student_id = s.id AND e.course_name = 'Math'
);
```

The subquery references the outer query (`s.id`). It checks if each student is enrolled in Math.

---

## Notes

* Subqueries can be nested at multiple levels
* Must return the correct number of values expected by the outer query
* Correlated subqueries can be slower—use only when necessary
* You can replace some subqueries with `JOINs` for better performance