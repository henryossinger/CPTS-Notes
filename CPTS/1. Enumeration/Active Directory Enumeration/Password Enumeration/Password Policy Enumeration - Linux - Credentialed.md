##### Policy can be pulled with valid domain credentials via the following: 
- CrackMapExec / rpcclient

#### Without valid credentials:
- SMB Null sessions: CrackMap, Enum4Linux, rpcclient
- LDAP Anonymous bind
----
## Commands:
##### SMB Null Sessions:
Enum4Linux: enum4linux -P 172.16.5.5
rpcclient -U "" -N 172.16.5.5 
	querydomaininfo

#### From Windows:
net use \\\host\ipc$ "Password" /u:"user"

##### Ldap Anonymous bind
windapsearch.py, ldapsearch, ad-ldapdomaindump.py

#### Windows:
PowerView/SharpView
net.exe
Example: net accounts