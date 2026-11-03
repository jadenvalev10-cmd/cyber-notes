# Access Control Worksheet: Payroll Incident

Google Cybersecurity Certificate activity

## Situation

I played the first cybersecurity hire at a growing business. A payroll deposit had gone to an unknown bank account. The finance manager said they didn't make a mistake, and the payment was stopped in time. The owner asked me to find out what happened so it wouldn't happen again.

## Task

Review the event log, work out who the likely threat actor was, find the access control problems that let it happen, and recommend fixes. I filled in an access controls worksheet with three columns: Note(s), Issue(s), and Recommendation(s).

## Action

- I read the event log. The user was Legal\Administrator, the event was "Payroll event added" (FAUX_BANK), and it happened on 10/03/2023 at 8:29:57 AM from the computer Up2-NoGud with the IP address 152.207.255.255.
- I compared the log to the employee directory. That IP matched Robert Taylor Jr., a legal attorney contractor whose contract ended on 12/27/2019. So either he used the account or someone else got hold of it.
- I noticed every employee in the directory had Admin authorization, including contractors, part-time and seasonal staff. That breaks the principle of least privilege, since a legal contractor had no reason to have admin or payroll access.
- I noticed accounts were never turned off when people left. Taylor's account was still active almost four years after his end date, and Joanne Phelps and Lei Chu (both ended 1/31/2020) were still listed with Admin access.
- I recommended role-based access control with least privilege, so only approved finance staff get admin and payroll access.
- I recommended an offboarding procedure that disables accounts the day someone leaves, plus quarterly access reviews to catch old accounts.
- I recommended multi-factor authentication on every account and a second person's approval for payroll changes.

## Result

The incident traced back to a former contractor's account that should have been disabled, and it could reach payroll because everyone had Admin rights. The recommendations go after the causes: too much access, no process for removing it, and weak authentication.

## Key terms

- **Authentication:** verifying who a user is.
- **Authorization:** what a user is allowed to access and do once they're verified.
- **Principle of least privilege:** users get only the minimum access they need to do their job.
- **Role-based access control (RBAC):** access is based on a user's job role.
- **Deprovisioning / offboarding:** removing a person's accounts and access when they leave.
- **Multi-factor authentication (MFA):** requiring more than one proof of identity to log in.
- **Event log:** a record of activity on a system, useful for spotting suspicious behavior and tracking users.
