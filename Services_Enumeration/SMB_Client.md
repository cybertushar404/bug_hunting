
## SMB Connect share
```
smbclient //IP_ADDRESS/share
smbclient //IP_ADDRESS/tmp
smbclient [\\\\IP_ADDRESS\\ipc](file://IP_ADDRESS/ipc) -U username_here
smbclient //IP_ADDRESS/ipc -U username_here 
smbclient -U '.' -L IP_ADDRESS
smbclient -U 'guest' -L IP_ADDRESS
```
Anonymous login:
```
smbclient //IP_ADDRESS/anonymous
```
Download file:
```
smbget -R smb://IP_ADDRESS/anonymous
```
Mount Share
```
mkdir /mnt/remote/
mount -t cifs //10.10.10.10/Backups /mnt/remote/
```

View available commands from the smb prompt:
<img width="674" height="220" alt="download" src="https://github.com/user-attachments/assets/1fc99caa-12a8-434c-9b63-130652f239be" />
