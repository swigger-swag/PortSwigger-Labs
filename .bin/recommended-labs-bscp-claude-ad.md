<div align="center">
<h1>BSCP Exam Preparation</h1>

The Burp Suite Certified Practitioner (BSCP)</div>

## Exam Format

- 4 hours, fully hands-on, proctored.
- Two independent web applications.
- Each application has three sequential stages: gain access as a regular user, escalate to administrator, read `/home/carlos/secret`.
- All six stages must be completed to pass; five out of six is a fail.
- No hints on vulnerability category, no lab reset.
- Open book: notes, internet, third-party tools, and Burp extensions are allowed.
- Burp Suite Professional required (Community edition lacks the scanner and features used in solving stages).

## Recommended PortSwigger Academy Labs

Work through every topic below at Apprentice and Practitioner level without looking at solutions first. Expert labs are optional but useful for the harder chained scenarios.

### SQL Injection
- SQL injection `UNION` attacks (retrieving data from other tables)
- Blind SQL injection with conditional responses
- Blind SQL injection with time delays
- SQL injection attack, querying the database type and version on `MySQL` and `Microsoft`
- Second-order SQL injection

### Authentication
- Username enumeration via different responses
- `2FA` broken logic
- Broken brute-force protection, IP block
- Password reset broken logic
- Password reset poisoning via middleware

### Path Traversal
- File path traversal, traversal sequences blocked with absolute path bypass
- File path traversal, validation of start of path

### Command Injection
- Blind OS command injection with time delays
- Blind OS command injection with output redirection

### Business Logic Vulnerabilities
- Excessive trust in `client-side` controls
- High-level logic vulnerability
- Inconsistent handling of exceptional input
- Insufficient workflow validation
- Authentication bypass via flawed state machine
- Infinite money logic flaw

### Information Disclosure
- Information disclosure in error messages
- Source code disclosure via backup files
- Authentication bypass via `information disclosure`

### Access Control
- Unprotected admin functionality
- URL-based access control can be circumvented
- Method-based access control can be circumvented
- User ID controlled by request parameter, with unpredictable user IDs
- Multi-step process with no access control on one step
- Referer-based access control

### Cross-Site Request Forgery (CSRF)
- CSRF where token validation depends on request method
- CSRF where token is not tied to the user session
- CSRF where SameSite Lax bypass via `GET`

### Cross-Origin Resource Sharing (CORS)
- CORS vulnerability with basic origin reflection
- CORS vulnerability with trusted null origin

### Clickjacking
- Basic clickjacking with `CSRF` token bypass
- Clickjacking with form input data prefilled from a URL parameter

### Cross-Site Scripting (XSS)
- Reflected, stored, and DOM XSS across all major sinks
- XSS with content-type restrictions, filter evasion
- Exploiting cross-site scripting to steal cookies and bypass CSP
- DOM XSS using web messages
- Stored XSS into HTML context with most tags and attributes blocked

### Cross-Site WebSocket Hijacking
- Manipulating WebSocket messages to exploit vulnerabilities
- Cross-site WebSocket hijacking

### CSP Bypass
- CSP with unsafe-inline in script-src
- CSP with a JSONP endpoint bypass

### XXE Injection
- Exploiting XXE to retrieve files
- Exploiting XXE to perform SSRF
- Blind XXE with out-of-band interaction
- `XInclude` attacks

### SSRF
- SSRF with blacklist-based input filter
- SSRF with whitelist-based input filter
- SSRF via the referer header

### Request Smuggling
- HTTP request smuggling, basic `CL.TE` and `TE.CL` vulnerabilities
- Exploiting HTTP request smuggling to bypass front-end security controls
- Exploiting HTTP request smuggling to reveal front-end request rewriting
- Exploiting HTTP request smuggling to perform web cache poisoning

### Web Cache Poisoning
- Web cache poisoning with an unkeyed header
- Web cache poisoning with multiple headers
- Parameter cloaking

### Insecure Deserialization
- Modifying serialized objects
- Using application functionality to exploit insecure deserialization
- Exploiting Java deserialization with Apache Commons
- Using PHAR deserialization to deploy an exploit chain

### GraphQL
- Accessing private GraphQL posts
- Finding a hidden GraphQL endpoint
- Bypassing GraphQL brute-force protections

### JWT Attacks
- JWT authentication bypass via unverified signature
- JWT authentication bypass via flawed signature verification
- JWT authentication bypass via weak signing key
- JWT authentication bypass via jwk header injection
- JWT authentication bypass via kid header path traversal

### OAuth
- Authentication bypass via `OAuth` implicit flow
- Forced OAuth profile linking
- OAuth account hijacking via `redirect_uri`

### File Upload
- Remote code execution via web shell upload
- Web shell upload via `Content-Type` restriction bypass
- Web shell upload via path traversal

### SSTI (Server-Side Template Injection)
- Basic server-side template injection
- SSTI in an unknown language with a documented exploit

### Prototype Pollution
- Client-side prototype pollution via browser APIs
- DOM XSS via client-side prototype pollution
- Server-side prototype pollution, detection in Node.js

### Race Conditions
- Limit overrun race conditions
- Bypassing rate limits via race conditions
- Multi-endpoint race conditions
- Partial construction race conditions

### NoSQL Injection
- Detecting NoSQL injection
- Exploiting NoSQL injection to extract data
- NoSQL injection to bypass authentication

### API Testing
- Exploiting an API endpoint using documentation
- Finding and exploiting an unused API endpoint
- Exploiting a mass assignment vulnerability

### Web Cache Deception
- Exploiting web cache deception to steal user data

## Study Approach

- Complete labs without solutions first; only check the solution after a genuine attempt
- Take the free PortSwigger practice exam repeatedly until consistently passing within time
- Practice mapping the application (target map, proxy history) in the first minutes rather than jumping straight to attacks
- Re-test every function and object after each new privilege level is obtained
- Keep minimal running notes per finding: endpoint, parameter, hypothesis, result
- Since the exam gives no hints on vulnerability class, drill breadth over depth across all categories rather than mastering a few deeply

## Potential Exam Web Attacks

Based on documented stage structure (access, admin, secret file) and community writeups, treat these as the core pool the exam draws from:

1. SQL injection (UNION, blind, second-order)
2. Authentication logic flaws (password reset, 2FA bypass, broken brute-force protection)
3. Access control bypass (IDOR, URL/method-based, multi-step process)
4. Business logic flaws (workflow bypass, state machine flaws)
5. Cross-site scripting (reflected, stored, DOM-based)
6. CSRF combined with a secondary flaw (SameSite bypass, token validation flaw)
7. Server-side request forgery (SSRF via internal pivot)
8. XML external entity injection (XXE, including blind/OOB)
9. Insecure deserialization (Java, PHP/PHAR object injection)
10. HTTP request smuggling (used to bypass front-end controls or poison cache)
11. Web cache poisoning
12. JWT attacks (algorithm confusion, weak key, jwk/kid injection)
13. OAuth misconfiguration (redirect_uri, implicit flow, account linking)
14. File upload leading to remote code execution
15. Server-side template injection
16. Prototype pollution (client-side or server-side)
17. Race conditions (limit overrun, multi-endpoint)
18. GraphQL misconfiguration
19. NoSQL injection
20. API misuse (undocumented endpoints, mass assignment)

Each application's three stages typically chain two or three of the above rather than relying on a single isolated bug, so plan for chaining a low-privilege foothold into a privilege escalation into a final file read.

## References

- PortSwigger Web Security Academy: https://portswigger.net/web-security
- BSCP official exam info: https://portswigger.net/web-security/certification
- BSCP practice exam: https://portswigger.net/web-security/certification/practice-exam