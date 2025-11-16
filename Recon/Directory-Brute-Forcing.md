## Gobuster
```
gobuster dir -u [TARGET-URL] -w /usr/share/wordlists/dirb/big.txt
```
## Feroxbuster
```
feroxbuster -u [TARGET-URL] -w /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt -x php,txt,html
```
For ASP.NET/IIS servers:
```
feroxbuster -u [TARGET-URL] -w /usr/share/seclists/Discovery/Web-Content/raft-medium-directories-lowercase.txt -x aspx
```
## Dirsearch
```
dirsearch -u [TARGET-URL] -w /usr/share/dirb/wordlists/common.txt
```
## FFUF
```
ffuf -u [TARGET-URL]/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt
```
Vhosts Fuzzing
```
ffuf -w /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u http://academy.htb:PORT/ -H 'Host: FUZZ.academy.htb'
```
Extension Fuzzing
```
 ffuf -w /opt/useful/SecLists/Discovery/Web-Content/web-extensions.txt:FUZZ -u http://SERVER_IP:PORT/blog/indexFUZZ
```
Recursive Fuzzing
```
ffuf -w /opt/useful/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://SERVER_IP:PORT/FUZZ -recursion -recursion-depth 1 -e .php -v
```
Sub-domain Fuzzing
```
ffuf -w /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u https://FUZZ.hackthebox.eu/
```
Bypass WAFs
```
ffuf -w payloads.txt -u https://target.com/FUZZ -H "X-Originating-IP: 127.0.0.1"
```
