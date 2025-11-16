## Nmap
Scan all ports:
```
nmap -sS -A -T4 -p 1-65535 -oA nmapscan.txt 10.10.10.20
```
Intense scan, all TCP ports, no ping:
```
nmap -p 1-65535 -T4 -A -v -Pn 10.10.10.12
```
Nmap scripting engine (NSE):
```
nmap --script=[scriptname] [host]
```
Detect WAF using NMAP:
```
nmap -p80 --script http-waf-detect [host]
```
Nmap Range Scan(pivoting):
```
nmap -sn -v 192.168.1-255
```
Nmap all basic scripts scan:
```
nmap -sV -Pn --script "default,vuln,auth,discovery,exploit,external,safe" example.com
```
