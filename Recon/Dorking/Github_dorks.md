# Here are few powerful GitHub dorks to use in real-world recon:
```
org:"target" path:**/.env 
org:"target" path:**/.git-credentials 
org:"target" path:**/config.json 
org:"target" path:**/docker-compose.yml 
org:"target" path:**/secrets.yml 
org:"target" path:**/.npmrc 
org:"target" path:**/id_rsa 
org:"target" path:**/wp-config.php 
org:"target" path:**/.bash_history 
org:"target" path:**/database.yml 
org:"target" path:**/.ssh/config 
org:"target" path:**/.htpasswd 
org:"target" path:**/env.local 
org:"target" path:**/.env.production 
org:"target" path:**/config.php 
org:"target" path:**/.bashrc 
org:"target" path:**/main.tf
org:"target" firebase 
org:"target" api_key 
org:"target" access_key 
org:"target" SECRET_KEY 
org:"target" password 
org:"target" credentials 
org:"target" AWS_SECRET_ACCESS_KEY 
org:"target" sendgrid 
org:"target" twilio 
org:"target" slack_token 
org:"target" private_key
```

# Config Files
```
org:(org_name_in_github) filename:config.js
org:(org_name_in_github) filename:settings.py
org:(org_name_in_github) filename:application.properties
org:(org_name_in_github) filename:credentials.json
org:(org_name_in_github) filename:firebase.json
```

# GitHub Actions
```
org:(org_name_in_github) filename:.github/workflows
org:(org_name_in_github) "secrets." language:yaml
org:(org_name_in_github) "GITHUB_TOKEN"
org:(org_name_in_github) "CI_SECRET"
```
# Hardcoded credentials (in code)
```
org:(org_name_in_github) "username" "password"
org:(org_name_in_github) "username"
org:(org_name_in_github) "password"
org:(org_name_in_github) "db_password"
org:(org_name_in_github) "mongodb+srv://"
org:(org_name_in_github) "postgres://"
org:(org_name_in_github) "mysql://"
```
# find Admin Panels too
```
org:(org_name_in_github) "admin"
org:(org_name_in_github) "admin" in:url
org:(org_name_in_github) "admin" in:path
org:(org_name_in_github) "dashboard" in:url
org:(org_name_in_github) "control panel"
org:(org_name_in_github) "login" filename:config.js
org:(org_name_in_github) "admin_url"
org:(org_name_in_github) "site_url"
```
