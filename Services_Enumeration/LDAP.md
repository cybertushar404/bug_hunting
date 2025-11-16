## Ports
- 389     LDAP (unencrypted or STARTTLS)
- 636     LDAPS (LDAP over SSL/TLS)

## Context discovery and general enumeration¶
Get base naming contexts
```
ldapsearch -H ldap://[IP-ADDRESS] -x -s base -b "" -LLL -o ldif-wrap=no namingcontexts
```
General search within the naming context
```
ldapsearch -H ldap://[IP-ADDRESS] -x -b "DC=[DOMAIN],DC=local"
```

## LDAP commands
Basic search with bind (replace placeholders accordingly)
```
ldapsearch -H ldap://[IP-ADDRESS] -D [USERNAME] -w [PASSWORD] -b "DC=HACKFAST,DC=LOCAL" > data.txt
```
Search base domain with anonymous bind
```
ldapsearch -h [IP-ADDRESS] -x -b "dc=[DOMAIN],dc=local"
```
Search for user objects
```
ldapsearch -h [IP-ADDRESS] -x -b "dc=[DOMAIN],dc=local" '(objectClass=user)'
```
Search for group objects
```
ldapsearch -h [IP-ADDRESS] -x -b "dc=[DOMAIN],dc=local" '(objectClass=group)'
```
Bypass TLS SNI check (LDAPS)
```
ldapsearch -H ldaps://[IP-ADDRESS]:636/ -x -s base -b '' "(objectClass=*)" "*" +
```

## Validate credentials
Validate using DOMAIN\USERNAME format
```
ldapsearch -x -H ldap://[IP-ADDRESS] -D '<DOMAIN>\\[USERNAME]' -w '[PASSWORD]' -b "DC=[DOMAIN],DC=local"
```
