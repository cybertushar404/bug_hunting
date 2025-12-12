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

### 𝗚𝗲𝘁 𝗦𝗵𝗼𝗱𝗮𝗻 𝗜𝗣𝘀 𝗳𝗼𝗿 𝗳𝗿𝗲𝗲 𝘄𝗶𝘁𝗵𝗼𝘂𝘁 𝗮𝗻 𝗔𝗣𝗜 𝗸𝗲𝘆
Shodan’s $5 API key gives 10k results for 1 month. 
But 𝗶𝗽𝗳𝗶𝗻𝗱𝗲𝗿 has no limit and works without an API key — you can scan all of your private program wildcards.

```
𝗨𝘀𝗶𝗻𝗴 𝗳𝘂𝗹𝗹 𝗦𝗵𝗼𝗱𝗮𝗻 𝗾𝘂𝗲𝗿𝘆 𝗳𝗼𝗿𝗺𝗮𝘁 (𝗮𝗱𝘃𝗮𝗻𝗰𝗲𝗱)
echo 'ssl:"nvidia.com"' | ipfinder --silent
echo 'hostname:"sqrx.com"' | ipfinder --silent
echo 'ssl.cert.subject.cn:"sqrx.com"' | ipfinder --silent
echo 'org:"FIDELITY NATIONAL INFORMATION SERVICES"' | ipfinder --silent
echo 'asn:"AS3614"' | ipfinder --silent
echo 'ip:"173.0.84.0/24"' | ipfinder --silent
echo 'http.favicon.hash:"816615992"' | ipfinder --silent
cat subs.txt | ipfinder --silent

𝗨𝘀𝗶𝗻𝗴 --𝗳𝗶𝗹𝘁𝗲𝗿 𝗳𝗹𝗮𝗴 (𝗯𝗲𝗴𝗶𝗻𝗻𝗲𝗿-𝗳𝗿𝗶𝗲𝗻𝗱𝗹𝘆)
echo "nvidia.com" | ipfinder --silent --filter ssl
echo "sqrx.com" | ipfinder --silent --filter hostname
echo "example.com" | ipfinder --silent --filter ssl.cert.subject.cn

𝗣𝗼𝗿𝘁 𝗦𝗰𝗮𝗻𝗻𝗶𝗻𝗴, 𝘆𝗼𝘂 𝗰𝗮𝗻 𝘂𝘀𝗲 𝗮𝗻𝘆 𝘁𝗼𝗼𝗹 𝗳𝗼𝗿 𝘁𝗵𝗶𝘀
echo "nvidia.com" | ipfinder --silent | portmap internetdb --silent
echo "nvidia.com" | ipfinder --silent | naabu -duc -silent -passive
```

links: https://github.com/rix4uni/portmap,
       https://github.com/rix4uni/ipfinder
