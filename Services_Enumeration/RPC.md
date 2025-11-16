## RPC Server Exploration
Connect to RPC server using rpcclient with null (anonymous) authentication
```
rpcclient -U "" -N [TARGET-IP] 
```
OR
```
rpcclient -U "[USERNAME]" [TARGET-IP] # With creds 
```

## RPCclient Enumeration-
Server information
```
srvinfo
```
Enumerate all domains that are deployed in the network
```
enumdomains
```
Enumerates all available shares
```
netshareenumall
```
Provides information about a specific share.
```
netsharegetinfo <share>
```
Provides information about a specific user
```
queryuser <RID>
```
