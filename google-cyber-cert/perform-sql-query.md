# Perform a SQL Query

Google Cybersecurity Certificate activity

## Situation

I was a security analyst looking through an organization's data in a MariaDB database called `organization`. It had a `machines` table and a `log_in_attempts` table. I needed to pull records out of them to look for anything suspicious in the login activity.

## Task

Use basic SQL to retrieve data from both tables, then sort the results so the login activity was easier to review.

## Action

**Retrieved everything from a table.** `SELECT * FROM machines;` returns every column and row. The `*` means all columns, and `FROM` says which table to use.

**Retrieved specific columns.** Listing column names after `SELECT` returns only those columns. This is useful when a table is large and I only care about a few fields.

**Looked at the login attempts.** I ran `SELECT * FROM log_in_attempts;` and scanned the countries and login times for anything that looked like a red flag, such as attempts from unexpected locations or at odd hours.

**Sorted the results.** `ORDER BY login_date, login_time` sorted the attempts in order of when they happened, which made patterns easier to see.

A few details I picked up: every statement ends with a semicolon, and table names are case-sensitive. Filtering with `WHERE` comes in the next labs.

## Result

I could pull whole tables, choose specific columns, and sort the output with `SELECT`, `FROM`, and `ORDER BY`. This is the starting point for investigating logs with SQL.

## Key terms

- **SELECT:** chooses which columns to return.
- **FROM:** chooses the table.
- **\*:** wildcard for all columns.
- **ORDER BY:** sorts the results.
- **Semicolon:** ends a SQL statement.
