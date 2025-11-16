Port: 21

## CheckList:
- Anonymous login
- Check default credentials
- Check version for exploit
- Check for files upon login
- Check for SSH keys or if you can access .ssh file
- Try uploading shell if reflected in web server.
- Brute force credentials

Check if anonymous FTP access is available:
```
ftp [host]
Username: anonymous
Password: anything
```
Lists available Nmap scripts
```
ls /usr/share/nmap/scripts/ \| grep "ftp"
```
FTP nse scripts:
```
nmap –script ftp-anon,ftp-bounce,ftp-libopie,ftp-proftpd-backdoor,ftp-vsftpd-backdoor,ftp-vuln-cve2010-4221,tftp-enum -p 21 10.0.0.1
```

Nmap scripts against a target IP on port 21 for comprehensive vulnerability scanning and information gathering.
```
nmap -p 21 --script ftp* [TARGET-IP]
```
