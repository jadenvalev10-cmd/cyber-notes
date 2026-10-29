# Apply Filters to SQL Queries

Google Cybersecurity Certificate activity

## Situation

I'm a security analyst at an organization that's working to make its systems more secure. I had two things to look into: suspicious login activity in the `log_in_attempts` table, and which employee machines in the `employees` table needed security updates.

## Task

Use SQL filters (`AND`, `OR`, `NOT`, and `LIKE`) to pull only the records I needed:

- Failed login attempts after business hours
- Login attempts on 2022-05-08 and 2022-05-09
- Login attempts from outside Mexico
- Marketing employees in the East building
- Employees in Finance or Sales
- Employees not in the IT department

## Action

**Failed logins after hours.** Failed logins outside business hours can point to someone trying to guess passwords when nobody is watching.

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE;
```

`AND` means both conditions have to be true. `login_time > '18:00'` keeps attempts after 18:00 (times use the 24-hour format), and `success = FALSE` keeps only the failed ones. A value of 0 works too.

**Logins on specific dates.** A suspicious event happened on 2022-05-09, so I wanted that day and the day before.

```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

I used `OR` because a row only has to match one of the two dates. `AND` would return nothing, since one login cannot happen on two days. Dates are written as `YYYY-MM-DD` inside single quotes.

**Logins outside of Mexico.** The team confirmed the activity did not come from Mexico, so I needed everything else.

```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

The `country` column has both `MEX` and `MEXICO`, so an exact match would miss one. `LIKE 'MEX%'` matches anything that starts with MEX (`%` is a wildcard for any number of characters), and `NOT` flips it to exclude those rows.

**Marketing employees in the East building.** Marketing machines needed a security update, but only the ones in the East building.

```sql
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
```

`department = 'Marketing'` is an exact match. `office LIKE 'East%'` matches East-170, East-320, and any other East office. `AND` requires both, so I only get Marketing employees in East.

**Employees in Finance or Sales.** A different update was needed for these two departments.

```sql
SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';
```

`OR` returns a row that matches either department.

**Employees not in IT.** IT already had the update, so I needed everyone else.

```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```

`NOT` excludes the IT rows and returns all other employees.

## Result

| Query | What it returns |
| --- | --- |
| Failed logins after 18:00 | Failed attempts outside business hours |
| Logins on 2022-05-08 or 2022-05-09 | Activity around the suspicious event |
| Logins outside Mexico | Attempts from every country except Mexico |
| Marketing in East offices | Marketing machines in the East building |
| Finance or Sales | Machines for those two departments |
| Not IT | Machines that still need the update |

Filtering with `AND`, `OR`, `NOT`, and `LIKE` gave me only the relevant records instead of whole tables, which made both the login investigation and the update planning faster and more accurate.

## Key terms

- **`WHERE`**: filters rows based on a condition.
- **`AND`**: both conditions must be true.
- **`OR`**: at least one condition must be true.
- **`NOT`**: excludes rows that match the condition.
- **`LIKE` and `%`**: matches a pattern; `%` stands for any number of characters.
- **Dates and times**: dates are `YYYY-MM-DD` and times are 24-hour, both in single quotes.
