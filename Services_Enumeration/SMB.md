- Port: 139,445

Connects to an SMB share using null authentication
```
smbclient //[IP-ADDRESS]/[SHARE] -N
```
scan SMB and netbios service :
```
sudo nbtscan -r 192.168.1.1-254 -v
```
OR
```
sudo nbtscan -r 192.168.50.0/24
```
OS detection:
```
sudo nmap 192.168.1.5 -sV -p T:139,445 U:137 --script="smb-os-discovery.nse" 
```
Nmap script:
```
nmap -p445 --script smb-enum-shares,smb-ls --script-args smbusername=administrator,smbpassword=smbserver_771 10.4.31.90
```
SMB Vulnerability Scan:
```
nmap -p 445 -vv --script=smb-enum-shares.nse,smb-ls.nse,smb-enum-users.nse,smb-mbenum.nse,smb-os-discovery.nse,smb-security-mode.nse,smb-vuln-cve2009-3103.nse,smb-vuln-ms06-025.nse,smb-vuln-ms07-029.nse,smb-vuln-ms08-067.nse,smb-vuln-ms10-054.nse,smb-vuln-ms10-061.nse,smb-vuln-regsvc-dos.nse 10.10.10.10
```
## User Enumeration
Enumerate users
```
crackmapexec smb [TARGET-IP] -u 'user' -p 'PASS' --users
```
Enumerate domain groups
```
crackmapexec smb [TARGET-IP] -u 'user' -p 'PASS' --groups
```
Enumerate local users
```
crackmapexec smb [TARGET-IP] -u 'user' -p 'PASS' --local-users
```

## Tool: smbmap
```
smbmap -H 10.129.14.128
```
## Tool: CrackMapExec
```
crackmapexec smb 10.129.14.128 --shares -u '' -p ''
```
## RCE via SMB with smbmap:
```
smbmap -H 10.10.10.10 -u administrator -p password123 -x 'ifconfig'
```
