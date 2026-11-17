# Deliverable 4 - Why secure coding matters

The `login.php` finding uses `md5()` for password hashing. If the database is exposed, MD5 hashes may be guessed quickly; adaptive password hashing would reduce that harm.

ZAP also flagged missing CSP and anti-clickjacking protections. These controls reduce common browser-side attacks. Prepared SQL statements, controlled uploads, and safe errors help prevent malicious input from becoming a security incident.

Result: SAST and DAST were completed against DVWA, and the cited issues were documented. These are findings and design risks, not proof that every attack is exploitable. DVWA was local in Docker; an isolated VM was not confirmed.
