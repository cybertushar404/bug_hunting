- Port: 161,162
## Table: Windows SNMP MIB values
| OID                   | Description       |
|-----------------------|-------------------|
| 1.3.6.1.2.1.25.1.6.0  | System Processes  |
| 1.3.6.1.2.1.25.4.2.1.2 | Running Programs  |
| 1.3.6.1.2.1.25.4.2.1.4 | Processes Path    |
| 1.3.6.1.2.1.25.2.3.1.4 | Storage Units     |
| 1.3.6.1.2.1.25.6.3.1.2 | Software Name     |
| 1.3.6.1.4.1.77.1.2.25  | User Accounts     |
| 1.3.6.1.2.1.6.13.1.3   | TCP Local Ports   |

Find Open ports of SNMP:
 ```
   nmap -sU --open -p 161 192.168.50.1-255 -oG open-snmp.txt
   ```
```
   nmap -sU -p 161 -sV -sC <ip>
   ```
```
   nmap -vv -sV -sU -Pn -p 161,162 --script=snmp-netstat,snmp-processes 10.10.10.10 check
  ```


OneSixtyOne:
*OneSixtyOne brute forces community strings based on dictionary and the target IP address. You can also provide a list of host IP addresses to be scanned by onesixtyone using the -i option. Single values can be passed via the command line.*
```
onesixtyone -c [community list] -i [host list]
```
SNMPwalk:
*SNMPwalk queries MIB values to retrieve information about managed devices. It requires a valid SNMP read-only community string.*

```
snmpwalk -c public -v1 [host] [MIB]
```
```
snmpwalk -c public -v1 192.168.50.151 1.3.6.1.4.1.77.1.2.25
```
Msfconsole:
```
use auxiliary/scanner/snmp/snmp_enum
```
Brute Force:
```
nmap -sU --open -p 161 192.168.1.0/24
```
```
onesixtyone -c community.txt 192.168.1.244
```
```
onesixtyone -c community.txt -i ips.txt
```
