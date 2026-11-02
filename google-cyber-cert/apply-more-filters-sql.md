# Apply More Filters in SQL

Google Cybersecurity Certificate activity

## Situation

I was a security analyst looking through the `log_in_attempts` table in the `organization` database (MariaDB). I needed to narrow the login records down by date, time, and event ID to investigate suspicious activity.

## Task

Use comparison operators and `BETWEEN` to filter login attempts by date, by time of day, and by event ID.

## Action

**Filtered by date.** I used `WHERE login_date > '2022-05-09'` to get everything after that day. That left out May 9 itself, so I changed it to `>=` to include it.

**Filtered by a date range.** `WHERE login_date BETWEEN '2022-05-09' AND '2022-05-11'` returned attempts within that range. `BETWEEN ... AND` includes both end values.

**Filtered by time.** `WHERE login_time < '07:00:00'` found attempts before the workday started. I then used `BETWEEN '06:00:00' AND '07:00:00'` to look at just that one hour.

**Filtered by event ID.** I selected `event_id`, `username`, and `login_date` and filtered with `WHERE event_id >= 100`, then `BETWEEN 100 AND 150` to narrow it down.

## Result

I could filter the login data by date, time, and number ranges. Combining these filters lets me zero in on activity outside normal hours or around a specific event.

## Key terms

- **Comparison operators:** `=`, `>`, `<`, `<>` (not equal), `>=`, `<=`.
- **BETWEEN ... AND:** a range filter that includes both ends.
- **Quoting:** dates and times go in single quotes. Numbers do not.
- **Date and time formats:** dates are YYYY-MM-DD and times are 24-hour.
