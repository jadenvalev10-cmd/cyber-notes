# Data Leak Worksheet: Least Privilege

Google Cybersecurity Certificate activity

## Situation

I worked for an educational technology company whose app helps teachers grade assignments automatically and handles data from schools, instructors, parents, and students. Internal business plans were leaked on social media. A sales manager had shared a folder of internal-only documents (an unannounced product, customer analytics, and promotional materials) with their team and never revoked access. During a video call, a sales representative meant to send a business partner a link to the promotional materials but sent the link to the whole folder. The partner posted it on their company's social media page.

## Task

Figure out what caused the leak, review how the company's security plan handles it, and recommend improvements to least privilege. I filled in a worksheet with four parts: Issue(s), Review, Recommendation(s), and Justification.

## Action

- I identified the factors behind the leak: the manager left access to the internal folder open after the meeting, so people had more access than they needed, and the representative shared the entire folder link by mistake. The partner then posted it publicly.
- I read the security plan snapshot. The company uses the NIST Cybersecurity Framework: the Protect function, the Data security category (PR.DS), and subcategory PR.DS-5, protections against data leaks. The control it points to is NIST SP 800-53: AC-6.
- I reviewed AC-6 (least privilege). It says users should only get the minimum access needed to do their task, so nobody operates at a higher privilege level than the job requires. Its control enhancements include restricting access by role, automatically revoking access after a period of time, keeping activity logs of provisioned accounts, and regularly auditing privileges.
- I picked two enhancements that would have prevented this leak: automatically revoke access after a period of time, and restrict access to sensitive resources by user role.
- I wrote a justification. Automatic revocation would have cut off the representative's access once the meeting ended, so the wrong link could not have been shared. Role-based restrictions would keep sensitive files like customer analytics limited to the people who need them, so fewer users could leak them.

## Result

The leak came from two failures: access that was never revoked, and a sharing mistake that nothing stopped. Automatic revocation and role-based access would both have limited the damage, and least privilege gets weaker the more people hold access without anyone checking.

## Key terms

- **Principle of least privilege:** users get only the minimum access and authorization needed to do their job.
- **Data leak:** information shared or exposed outside the people it was meant for, often by accident.
- **NIST SP 800-53:** NIST guidelines that give organizations a customizable information privacy plan, made up of controls.
- **AC-6:** the least privilege control in SP 800-53 (sixth in the access control category).
- **Control enhancement:** a suggested improvement that makes a control work better.
- **Role-based access:** access to resources is based on a user's job role.
- **Automatic revocation:** access ends on its own after a set period.
