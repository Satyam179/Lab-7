# Deliverable 1 - STRIDE threat model

Application: DVWA at http://localhost:4280 (local Docker container). Browser input crosses a trust boundary into DVWA's PHP service, which sends SQL to MariaDB and writes uploads to local storage. A local-only port binding was observed; a dedicated VM was not demonstrated.

| STRIDE | Threat (source/assumption) | Mitigation |
|---|---|---|
| Spoofing | MD5 password hashing in login.php may aid credential compromise after a hash leak | Use password_hash() / password_verify(); protect sessions |
| Tampering | Low-mode SQLi handler interpolates request id into SQL | Use prepared statements and validate input |
| Repudiation | Audit logging coverage not verified (modeled threat) | Log logins, changes and uploads on server |
| Information disclosure | ZAP flagged leaked version information in response headers | Suppress unnecessary headers and detailed errors |
| Denial of service | Low-mode upload code has no application-side size check (modeled threat) | Enforce max file size, disk quotas and rate limits |
| Elevation of privilege | Weak cookie attributes / CSRF configuration may increase risk | Set Secure, HttpOnly, SameSite; CSRF and role checks |

DFD image: `01_Threat_Model_DFD.png`.
