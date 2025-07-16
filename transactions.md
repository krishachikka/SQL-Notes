# SQL Transactions

A transaction is a group of SQL statements that are executed as a single unit. Either all of them succeed, or none do.

---

## Why Use Transactions?

- To maintain **data integrity**
- To prevent incomplete or broken updates
- Especially useful in financial systems or multi-step processes

---

## Key Commands

### BEGIN / START TRANSACTION

Starts a new transaction block.

```sql
BEGIN;
````

### COMMIT

Saves all changes made during the transaction.

```sql
COMMIT;
```

### ROLLBACK

Undo all changes made during the transaction.

```sql
ROLLBACK;
```

---

## Example

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 1000
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE account_id = 2;

COMMIT;
```

If something goes wrong (like the second update fails), you can call:

```sql
ROLLBACK;
```

This will undo both updates.

---

## ACID Properties

Transactions follow four key principles:

* **Atomicity**: All operations succeed or none do
* **Consistency**: The database moves from one valid state to another
* **Isolation**: Transactions don’t interfere with each other
* **Durability**: Once committed, changes are permanent

---

## Auto-commit Mode

* In some databases, each SQL statement is committed automatically
* You may need to disable auto-commit to use manual transactions

```sql
SET autocommit = 0;
```

---

## Savepoints

Allows partial rollbacks within a transaction.

```sql
SAVEPOINT sp1;

-- some statements

ROLLBACK TO sp1;
```

---

## Notes

* Use transactions for anything that spans multiple steps or tables
* Always commit when done, or rollback if something fails
* Be cautious: forgetting to commit can lock resources

---
[← Indexes](./indexes.md) | [Next → Practice Questions](./practice.md)