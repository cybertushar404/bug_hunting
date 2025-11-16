- Port 3306

Try to login to MYSQL target:
```
mysql -h 10.10.10.10 -u root -p
```
## Remote MySQL Access 
With Password	
```
mysql -u [USERNAME] -p -h [TARGET-IP] -P 3306
```
Specify database (-D)	
```
mysql -u [USERNAME] -p -h [TARGET-IP] -D database_name
```
MySQL nmap scripts:
```
nmap -sV -Pn -vv  10.10.10.10 -p 3306 --script mysql-audit,mysql-databases,mysql-dump-hashes,mysql-empty-password,mysql-enum,mysql-info,mysql-query,mysql-users,mysql-variables,mysql-vuln-cve2012-2122
```

## MySQL Command Line Enumeration
Lists all databases on the MySQL server.  
```
SHOW DATABASES;
```
Switches to a specific database.  
```
USE database_name;
```
Displays all tables in the current database.  
```
SHOW TABLES;
```
Lists all columns in a specific table.    
```
SHOW COLUMNS FROM table_name;
```
Retrieves data from a table.  
```
SELECT * FROM table_name;
```
