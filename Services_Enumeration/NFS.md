- Port: NFS->2049
- RPC->111

Manual:

to check if thare is RPC
```
rpcinfo -p 192.168.1.9
```
this technic help us to transfer all files from victim to attacker
```
sudo showmount -e 192.168.1.9
```
```
sudo service rpc start
```
and create diresctory to transfer data to it
```
sudo mount -t nfs 192.168.1.9:/ /tmp/meta
umount /tmp/meta
```
Enumerate NFS shares:

```
nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount 10.10.10.10
```
```
sudo nmap --script nfs* 10.129.14.128 -sV -p111,2049
```
Show Available NFS Shares:
```
showmount -e 10.10.10.20
```

## Mount Share
1. Enumerating RPC Services
```
rpcinfo -p [IP-ADDRESS]
```
<img width="329" height="517" alt="1" src="https://github.com/user-attachments/assets/f925492d-49d3-4526-a21f-5dba2f5c4771" />

2. Running NSE Scripts to Enumerate RPC Services
```
nmap -sV --script=nfs-* [IP-ADDRESS]
```
3. Enumerate shares With showmount command
```
showmount -e [IP-ADDRESS]
```
4. Create a Directory for Mounting the Share
```
mkdir /tmp/nfs
```
5. Mount the NFS Share to the New Directory
```
sudo mount -t nfs [IP-ADDRESS]:/home/share /tmp/nfs -nolock
```
6. Navigate to the mounted directory to access the NFS share:
```
cd /tmp/nfs
```
