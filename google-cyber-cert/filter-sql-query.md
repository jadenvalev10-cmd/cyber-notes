# Filter a SQL Query

Google Cybersecurity Certificate activity

## Situation

I was a security analyst working in the `organization` database in MariaDB, using the `machines` and `employees` tables. Instead of reading whole tables, I needed to filter down to only the records that mattered.

## Task

Use `WHERE` to filter records, first with exact matches and then with pattern matching using `LIKE`.

## Action

**Checked the table structure.** `DESCRIBE` shows the columns in a table and their data types, so I knew what I could filter on.

**Filtered with an exact match.** `WHERE` keeps only the rows that meet a condition, and `=` matches an exact value. Text values go in single quotes, for example `WHERE operating_system = 'OS 2'` or `WHERE department = 'Finance'`. Column names are not quoted.

**Filtered with patterns.** `LIKE` uses the `%` wildcard, which stands for any number of characters:

- `LIKE 'South%'` matches values that start with South.
- `LIKE '%South'` matches values that end with South.
- `LIKE '%South%'` matches values that contain South anywhere.

I used this on office locations to pull every office in a region without needing to know each exact name.

## Result

I could narrow tables down to specific machines and employees using `WHERE`, exact matches, and `LIKE` patterns. Filtering saves time and cuts out the noise when I'm investigating.

## Key terms

- **DESCRIBE:** shows a table's columns and types.
- **WHERE:** filters rows by a condition.
- **= :** exact match, with text in single quotes.
- **LIKE:** pattern match.
- **% wildcard:** any number of characters, placed at the start, end, or both.
