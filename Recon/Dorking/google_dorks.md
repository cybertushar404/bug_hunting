Simple Dork
```
site:target.com inurl:login | inurl:signin | intitle:Login | intitle: signin | inurl:auth
```
Advanced Dork
```
site:*<*.target.com intext:"login" | intitle:"login" | inurl:"login" | intext:"username" | intitle:"username" | inurl:"username" | intext:"password" | intitle:"password" | inurl:"password"
```
Wordpress Dorking
```
site:target.com inurl:wp- | inurl:wp-content | inurl:plugins | inurl:uploads | inurl:themes | inurl:download
```
Swagger-UI Dorking
```
Api Docs→ inurl:apidocs | inurl:api-docs | inurl:swagger | inurl:api-explorer site:"target.com"
```
Configuration Files Dorking
```
site:target.com ext:xml | ext:conf | ext:cnf | ext:reg | ext:inf | ext:rdp | ext:cfg | ext:txt | ext:ora | ext:ini
```
SQL Error Based Dork
```
site:flipkart.com intext:"sql syntax near" | intext:"syntax error has occurred" | intext:"incorrect syntax near" | intext:"unexpected end of SQL command" | intext:"Warning: mysql_connect()" | intext:"Warning: mysql_query()" | intext:"Warning: pg_connect()"
```
Documents Dork
```
site:target.com ext:doc | ext:docx | ext:odt | ext:pdf | ext:rtf | ext:sxw | ext:psw | ext:ppt | ext:pptx | ext:pps | ext:csv
```
Third Party Exposure
```
site:http://ideone.com | site:http://codebeautify.org | site:http://codeshare.io | site:http://codepen.io | site:http://repl.it | site:http://justpaste.it | site:http://pastebin.com | site:http://jsfiddle.net | site:http://trello.com | site:*.atlassian.net | site:bitbucket.org "target.com"
```
Sensitive info leak via google dork
```
site:.target.com ( "date of birth" OR confidential OR "internal use only" OR  "balance sheet" OR "profit and loss" OR  "banking details" OR  "source code" OR "national id" OR "top secret" ) (ext:pdf OR ext:doc OR ext:ppt OR ext:txt OR ext:csv) 
```
Google Dork - Sensitive Data
```
inurl:email= | inurl:phone= | inurl:name= | inurl:user= inurl:& site:example[.]com
```
Google Dork - Exposed Configs 🔍
```
site:example[.]com ext:log | ext:txt | ext:conf | ext:cnf | ext:ini | ext:env | ext:sh | ext:bak | ext:backup | ext:swp | ext:old | ext:~ | ext:git | ext:svn | ext:htpasswd | ext:htaccess | ext:json
```
Google Dork - XSS Prone Parameters 🔥
```
site:example[.]com inurl:q= | inurl:s= | inurl:search= | inurl:query= | inurl:keyword= | inurl:lang= inurl:&
```
Test for XSS in param value:
```
'"><img src=x onerror=alert()> 
```
Google Dork for File Uploads:
```
site:example[.]com intext:"choose file" | intext:"select file" | intext:"upload PDF"
```
Google Dork - Cloud File Shares:
```
site:http://drive.google.com "example[.]com"  
site:http://docs.google.com inurl:"/d/" "example[.]com"  
site:http://dropbox.com/s "example[.]com"  
```
Spreadsheets: check Spreadsheets permission is set to Editor 
```
site:*.target.com intext:"docs.google.com/spreadsheets"
```
This Google Dork Exposes Internal Test Environments 🔥
```
inurl:test | inurl:env | inurl:dev | inurl:staging | inurl:sandbox | inurl:debug | inurl:temp | inurl:internal | inurl:demo site:example[.]com
```
Credentials / Config
```
site:example.com filetype:env "DB_PASSWORD" OR "API_KEY"
site:example.com filetype:properties "password=" "jdbc"
site:example.com inurl:"/config.php" OR inurl:"/.env"
site:example.com inurl:/.env OR inurl:/config
```
Source control / Repo metadata
```
site:example.com inurl:".git/" "index"
site:example.com inurl:".svn/" OR inurl:".hg/"
site:example.com "git-credentials" OR "id_rsa"
```
Cloud storage / Buckets / Object leaks
```
site:example.com inurl:"storage.googleapis.com" OR inurl:"s3.amazonaws.com/example.com"
site:example.com filetype:json "google-services.json" OR "firebase"
site:example.com inurl:"/download?file=" "s3.amazonaws.com"
```
Logs / Error pages / Stack traces
```
site:example.com filetype:log "ERROR" OR "Exception"
site:example.com intext:"Stacktrace" OR "at com."
site:example.com intext:"ORA-" OR intext:"SQLSTATE" OR intext:"SQLException"
```
CI/CD / Build artifacts / Metadata
```
site:example.com filetype:yml "github" OR "actions" OR "secrets"
site:example.com filetype:jar "META-INF" "MANIFEST.MF"
site:example.com filetype:war OR filetype:ear "WEB-INF" "web.xml"
```
Admin consoles / Management endpoints
```
site:example.com intitle:"Admin Login" OR inurl:"/admin" "login"
site:example.com inurl:"/phpmyadmin/" OR inurl:"/adminer/"
site:example.com inurl:":8080" "Tomcat" OR "Manager"
```
API docs / GraphQL / Internal APIs
```
site:example.com inurl:graphql "playground" OR "graphiql"
site:example.com inurl:"/internal-api" OR inurl:"/private-api"
site:example.com inurl:api intext:token OR intext:"Authorization: Bearer"
```



