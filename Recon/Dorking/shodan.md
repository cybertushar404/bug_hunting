1.Initialize Shodan with your API Key

## Blocks of code

```
shodan init API_KEY_HERE
```

### hostname filtering
```
shodan download results.json.gz "hostname:target.com"
```
### ssl certificate filtering
``` 
shodan download results2.json.gz "ssl.cert.subject.cn:target.com"
```

``` 
shodan parse results.json.gz --fields ip_str > ips.txt
 ```

2.Shadow/Hidden HTTP services running on ports (excluding 80,443)

### download in json compressed format
```
shodan download shadow-http.json.gz "hostname:target.com http -port:80 -port:443"
```

```
shodan download shadow-http2.json.gz "ssl.cert.subject.cn:target.com http -port:80 -port:443"
```

### extract the IPs from it
```
shodan parse shadow-http.json.gz --fields ip_str > shadow_http_ips.txt
```

