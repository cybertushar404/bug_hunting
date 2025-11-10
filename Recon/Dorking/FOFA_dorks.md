# Here are some advanced FOFA dorks I use to uncover assets & exposures 
### ORG-WIDE / CERT PIVOTS
```
cert.subject="target.com" || cert.subject="*.target.com"
```
```
cert.subject="target.com" && protocol="https" && port="443"
```
```
domain="target.com" || cert.subject="target.com" || header="target.com" 
```
### DEV/STAGE/QA SURFACING (common env keywords)
```
domain="target.com" && (host="dev.*" || host="stg.*" || host="qa.*" || host="test.*")
```
### DIRECTORY LISTING / BACKUPS
```
domain="target.com" && title="Index of /" && body="Parent Directory"
```
```
domain="target.com" && (title="Index of /backup" || title="Index of /backups" || title="Index of /old")
```
```
domain="target.com" && (title="Index of /.git" || body=".git/HEAD")
```
```
domain="target.com" && (title="Index of /.svn" || body="/.svn/entries")
```
### SECRETS/SPILLS IN TEXT/JS
```
domain="target.com" && header="Content-Type: application/javascript" && body="apiKey"
```
```
domain="target.com" && (body="AWS_ACCESS_KEY_ID" || body="AKIA")
```
```
domain="target.com" && body="APP_KEY="           
```
```
domain="target.com" && body="PRIVATE KEY-----"
```      
```
domain="target.com" && body="eyJhbGciOi"          # JWT in responses
```
```
domain="target.com" && body="//# sourceMappingURL="    # JS source maps
```
### AUTH/SSO/OAUTH PIVOTS
```
domain="target.com" && (body="/oauth/authorize" || body="OpenID Connect" || body="/.well-known/openid-configuration")
```
### CORS MISCONFIG (weak but good lead list)
```
domain="target.com" && header="Access-Control-Allow-Origin: *" && header="Access-Control-Allow-Credentials: true"
```
### GRAPHQL / SWAGGER / API EXPLORERS
```
domain="target.com" && (title="GraphQL Playground" || title="GraphiQL" || body="graphql?query=")
```
```
domain="target.com" && (title="Swagger UI" || body="swagger-ui" || body="openapi")
```
### DEBUG / STACK TRACE FINGERPRINTS
```
domain="target.com" && (title="Whitelabel Error Page" || body="There was an unexpected error (type=)")
```
```
domain="target.com" && body="Traceback (most recent call last)"
```
```
domain="target.com" && (body="PHP Notice:" || body="PHP Warning:" || body="phpinfo()")
```
### CLOUD/EDGE FINGERPRINTS (useful for SSRF/CDN bypass trails)
```
domain="target.com" && header="X-Amzn-Trace-Id"
```
```
domain="target.com" && header="X-Envoy-Upstream-Service-Time"
```
```
domain="target.com" && header="Server: nginx" && header="Via: varnish"
```
### ELASTIC / LOGGING / METRICS / CI
```
domain="target.com" && (title="Kibana" || header="kbn-name")
```
```
domain="target.com" && title="Grafana" && body="Sign in"
```
```
domain="target.com" && title="Prometheus Time Series Collection and Processing Server"
```
```
domain="target.com" && title="Jenkins" && body="Login"
```
```
domain="target.com" && title="SonarQube"
```


















