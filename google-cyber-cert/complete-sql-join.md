# Complete a SQL Join

Google Cybersecurity Certificate activity

## Situation

I was a security analyst working with the `organization` database in MariaDB. The data I needed was split across three tables: `machines`, `employees`, and `log_in_attempts`. To investigate, I had to combine them.

## Task

Use joins to combine data from related tables, and compare how the different join types decide which rows to keep.

## Action

**INNER JOIN (machines and employees).** I joined the two tables on the shared `device_id` column:

```sql
SELECT *
FROM machines
INNER JOIN employees ON machines.device_id = employees.device_id;
```

An inner join only returns rows that have a match in both tables. I used dot notation (`table.column`) so SQL knew which table's column I meant.

**LEFT JOIN and RIGHT JOIN.** I ran the same join with `LEFT JOIN`, which keeps every machine and shows NULL for the employee if a machine is not assigned to anyone. With `RIGHT JOIN` it keeps every employee and shows NULL for the machine if they have none.

**INNER JOIN (employees and log_in_attempts).** I joined these on `username` to connect login attempts to the employee who made them:

```sql
SELECT *
FROM employees
INNER JOIN log_in_attempts ON employees.username = log_in_attempts.username;
```

## Result

I joined three tables and saw how each join type changes the output. Joins matter for security work because the information I need, like who owns a machine and who logged in, is usually split across tables.

## Key terms

- **Join:** combines rows from two tables using a shared column.
- **INNER JOIN:** only rows that match in both tables.
- **LEFT JOIN:** all rows from the left table, plus matches from the right.
- **RIGHT JOIN:** all rows from the right table, plus matches from the left.
- **Dot notation:** `table.column` avoids confusion when both tables have a column with the same name.
- **SELECT \*:** returns the shared column twice, once from each table.
- **Swapping table order:** a LEFT JOIN with the tables swapped gives the same result as a RIGHT JOIN.
