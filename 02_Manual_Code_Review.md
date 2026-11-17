# Deliverable 2 - Manual secure code review checklist

| Area | Status | Observed source | Recommended correction |
|---|---|---|---|
| Input handling | Needs fix | vulnerabilities/sqli/source/low.php: id is inserted into SQL string | Parameterized query |
| Authentication | Needs fix | login.php line 27: md5($pass) | password_hash() and password_verify() |
| Error handling | Needs fix | login.php can expose mysqli_error() using die() | Generic user error; internal logging |
| Resource management | Needs fix | vulnerabilities/upload/source/low.php calls move_uploaded_file without checking size/type | Limit file sizes, types and disk use |
| Secure defaults | Needs fix | ZAP reported missing CSP and anti-clickjacking header | Add restrictive CSP/frame-ancestors and validate policy |
| CSRF at login | Present | login.php uses checkToken() | Keep token checks on state changes |

Reviewed source: local SonarQube MD5 screenshot plus public digininja/DVWA source for the listed PHP files. This is a targeted review of those paths, not all 185 scanned files.
