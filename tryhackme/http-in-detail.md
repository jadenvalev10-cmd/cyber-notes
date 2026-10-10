# TryHackMe: HTTP in Detail

Pre Security path, How The Web Works module. September 2026.

**Situation:** Seven-task room on how browsers and web servers communicate, ending with a request emulator.

**Task:** Learn the structure of HTTP and HTTPS (URLs, requests, responses, methods, status codes, headers, cookies) and build correct requests.

**Action:**

- Task 1, URLs: HTTP is HyperText Transfer Protocol; HTTPS adds encryption. A URL has a scheme, optional user, host, port (80 for HTTP, 443 for HTTPS), path, query string (after `?`), and fragment (after `#`).
- Task 2, requests and responses:
  - A request has a request line (method, path, version), headers (Host, User-Agent, Referer), a blank line, and an optional body.
  - A response has a status line (for example `HTTP/1.1 200 OK`), headers (Server, Date, Content-Type, Content-Length), a blank line, and the body.
- Task 3, methods: GET retrieves, POST submits or creates, PUT updates, DELETE removes.
- Task 4, status codes: 1xx informational, 2xx success, 3xx redirect, 4xx client error (400, 401, 403, 404, 405), 5xx server error (500, 503).
- Task 5, headers: request headers include Host, User-Agent, Content-Length, Accept-Encoding, and Cookie; response headers include Set-Cookie, Cache-Control, Content-Type, and Content-Encoding.
- Task 6, cookies: HTTP is stateless, so the server sends a Set-Cookie header and the browser returns it in the Cookie header on later requests. Cookies often hold a session ID.
- Task 7, emulator: built GET, POST, PUT, and DELETE requests with the right path and parameters.

**Result:** Completed all seven tasks. Areas to revisit: request vs response headers, and why cookies are needed given that HTTP is stateless.

**Key terms**

HTTP, HTTPS, URL, scheme, port, query string, fragment, request line, status code, GET, POST, PUT, DELETE, User-Agent, Host, Content-Type, Set-Cookie, Cookie, stateless, session ID
