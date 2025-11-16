## Nmap Script:
Lists available Nmap scripts that target RDP services
```
ls -la /usr/share/nmap/scripts \| grep "rdp"
```
Enumerates encryption methods supported by the RDP server
```
nmap --script rdp-enum-encryption -p 3389 [IP_ADDRESS]
```
OR
```
nmap -sV -sC 10.129.201.248 -p3389 --script rdp*
```
RDP Security Check
Tool:rdp-sec-cehck
```
./rdp-sec-check.pl 10.129.201.248
```
Initiate an RDP Session
```
xfreerdp /u:cry0l1t3 /p:"P455w0rd!" /v:10.129.201.248
```
```
evil-winrm -i 10.129.201.248 -u Cry0l1t3 -p P455w0rD!
```
