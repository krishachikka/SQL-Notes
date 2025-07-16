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

---
[← Tables](./table.md) | [Next → Joins](./joins.md)