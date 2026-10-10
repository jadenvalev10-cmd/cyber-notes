# TryHackMe: How Websites Work

Pre Security path, How The Web Works module. October 2026.

**Situation:** Room covering the front-end building blocks of a website (HTML for structure, JavaScript for behaviour), sensitive data exposure, and HTML injection. The final task had a name field passed to a JavaScript function with no input sanitising.

**Task:** Understand how websites are built and how unsanitised input can be abused, by injecting HTML into a vulnerable page.

**Action:**

- Reviewed how HTML structures a page and how JavaScript changes it in the browser.
- Looked at sensitive data exposure: information that should not be visible to users ending up in client-side code.
- Exploited the unsanitised name field by entering HTML instead of a name, which the page rendered as live markup.

**Result:** Completed the room. This was the last room of the How The Web Works module. The fix for HTML injection is to sanitise or strip HTML from user input before using it.

**Key terms**

HTML, JavaScript, HTML injection (unfiltered input treated as code), input sanitisation, client-side vulnerability, sensitive data exposure
