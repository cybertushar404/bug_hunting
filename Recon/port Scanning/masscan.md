Fast recon of top 100 ports on a /16 subnet
```
masscan 192.168.0.0/16 --top-ports 100 --rate 5000 -oJ scan.json
```
Full port scan on one host for deeper analysis
```
masscan 10.0.0.5 -p0-65535 --rate 2000 -oJ fullscan.json
```
