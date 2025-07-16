# SQL Views

A **View** is a virtual table based on a `SELECT` query. It doesn’t store data itself, but fetches it from one or more tables.

---

## Why Use Views?

- Simplify complex queries
- Reuse common query logic
- Improve security by hiding certain columns
- Present data in a specific format without modifying actual tables

---

## Syntax: Creating a View

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;
````

### Example

```sql
CREATE VIEW active_students AS
SELECT id, name, city
FROM students
WHERE status = 'active';
```

Now you can query the view like a regular table:

```sql
SELECT * FROM active_students;
```

---

## Updating a View

You can modify a view by dropping and recreating it:

```sql
DROP VIEW active_students;

CREATE VIEW active_students AS
SELECT id, name
FROM students
WHERE age >= 18;
```

Some databases also support:

```sql
CREATE OR REPLACE VIEW view_name AS ...
```

---

## Dropping a View

```sql
DROP VIEW view_name;
```

---

## Updatable Views

Some views allow data manipulation (`INSERT`, `UPDATE`, `DELETE`) if:

* The view is based on a single table
* It doesn't use `DISTINCT`, `GROUP BY`, aggregate functions, or subqueries

### Example:

```sql
UPDATE active_students
SET city = 'Delhi'
WHERE id = 102;
```

This works only if the underlying `students` table allows it.

---

## Notes

* Views don’t store data—they just show a live result of a query
* Useful for abstracting business logic
* Can help enforce access control by showing only specific columns/rows