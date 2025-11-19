
# js finder
Getjs
```
cat subdomains_alive.txt | getJS | sort -u > live_getjs_js.txt
```
GetAllURLs (gau)
```
gau --subs < subdomains.txt | grep -E '\.js([?#].*)?$' | sort -u > archive_gau_js.txt
```
Waybackurls
```
waybackurls < subdomains.txt | grep -E '\.js([?#].*)?$' | sort -u > archive_wayback_js.txt
```
JS file hunting:
```
echo example.com | katana -d 3 | grep -E "\.js$" | nuclei -t /home/coffinxp/nuclei-templates/http/exposures/ -c 30
```
```
cat jsfiles.txt | grep -r -E "aws_access_key|aws_secret_key|api key|passwd|pwd|heroku|slack|firebase|swagger|aws_secret_key|aws key|password|ftp password|jdbc|db|sql|secret jet|config|admin|pwd|json|gcp|htaccess|.env|ssh key|.git|access key|secret token|oauth_token|oauth_token_secret" 
```
```
cat allurls.txt | grep -E "\.js$" | httpx-toolkit -mc 200 -content-type | grep -E "application/javascript|text/javascript" | cut -d' ' -f1 | xargs -I% curl -s % | grep -E "(API_KEY|api_key|apikey|secret|token|password)"
```
## jsleak is a tool to find secret , paths or links in the source code
```
cat urls.txt | jsleak -l -s -c 30
```
