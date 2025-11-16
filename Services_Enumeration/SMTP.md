- Port: 25
### simple mail transfere protocol:
*You can connect to an SMTP server with netcat and run the vrfy command to check if email addresses are valid. You can also check mailing list membership with expn*

SMTP nmap scripts:
```
nmap --script smtp-commands,smtp-enum-users,smtp-vuln-cve2010-4344,smtp-vuln-cve2011-1720,smtp-vuln-cve2011-1764 -p 25 10.0.0.1
```
Checks if SMTP server is an open relay, which could be abused to send spam emails
```
nmap -p 25 --script smtp-open-relay [TARGET-IP]
```
Enumerates users on an SMTP server using the VRFY command to gather potential email targets
```
nmap -p 25 --script smtp-enum-users --script-args smtp-enum-users.methods={VRFY} [TARGET-IP]
```

## Script to automate this service:
```
#!/usr/bin/python
import socket
import sys
if len(sys.argv) != 3:
print("Usage: vrfy.py <username> <target_ip>")
sys.exit(0)
# Create a Socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# Connect to the Server
ip = sys.argv[2]
connect = s.connect((ip,25))
# Receive the banner
banner = s.recv(1024) 
print(banner)
# VRFY a user
user = (sys.argv[1]).encode()
s.send(b'VRFY ' + user + b'\r\n')
result = s.recv(1024)
print(result)
# Close the socket
s.close()
```
Run  the follwing coomand and change the username
```
python3 smtp.py johndoe 192.168.50.8
```
