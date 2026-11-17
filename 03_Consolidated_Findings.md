# Deliverable 3 - Consolidated vulnerability findings (DVWA)

## SonarQube SAST
Security issues: 55; Reliability issues: 65; Maintainability issues: 27. High-severity example: weak MD5 hashing in `login.php` line 27. Additional High issues reported in the Dockerfile and `dvwa/includes/dvwaPage.inc.php`.

## OWASP ZAP DAST
Spider: 22 URLs found; 10 nodes added. Active scan: 100%, 3,033 requests. The exported report screenshot showed 0 High, 5 Medium, 7 Low and 5 Informational alert types. ZAP's raw scan also displayed 182 new alert instances; this is not a count of distinct vulnerability types.

| Severity | Tool | Finding | Potential impact |
|---|---|---|---|
| High | SonarQube | Weak hash MD5, login.php:27 | Password cracking if stored hashes are stolen |
| Medium | ZAP | Content Security Policy header not set | Increased script injection risk |
| Medium | ZAP | Anti-clickjacking header missing | Clickjacking through framing |

Other scan alerts include anti-CSRF token absence, parameter tampering, cookie attribute warnings and information leakage. Automated findings require manual validation.
