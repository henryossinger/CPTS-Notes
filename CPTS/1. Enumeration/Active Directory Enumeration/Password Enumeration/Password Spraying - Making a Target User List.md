- Note: 172.16.5.5 = DC IP
## Ways to gather usernames:
- Keberute with wordlist (statistically-likely-usernames)
- LLMNR + NBT-NS poisoning
- SMB Null Sessions
- LDAP Anonymous binds

#### SMB Null sessions:
```
enum4linux -U 172.16.5.5  | grep "user:" | cut -f2 -d"[" | cut -f1 -d"]"
```
```
rpcclient -U "" -N 172.16.5.5

rpcclient $> enumdomusers 
```
```
crackmapexec smb 172.16.5.5 --users
```

#### LDAP Anonymous Bind
```
ldapsearch -h 172.16.5.5 -x -b "DC=INLANEFREIGHT,DC=LOCAL" -s sub "(&(objectclass=user))"  | grep sAMAccountName: | cut -f2 -d" "
```
```
./windapsearch.py --dc-ip 172.16.5.5 -u "" -U
```

#### Keberute
```
kerbrute userenum -d inlanefreight.local --dc 172.16.5.5 /opt/jsmith.txt
```

Utilize Kerberos Pre-Authentication. For user enumeration, it sends TGT's to the DC with the specified wordlist.

Using Kerbrute for username enumeration will generate event ID [4768: A Kerberos authentication ticket (TGT) was requested](https://docs.microsoft.com/en-us/windows/security/threat-protection/auditing/event-4768). This will only be triggered if [Kerberos event logging](https://docs.microsoft.com/en-us/troubleshoot/windows-server/identity/enable-kerberos-event-logging) is enabled via Group Policy.

## If we have credentials: 
```
sudo crackmapexec smb 172.16.5.5 -u htb-student -p Academy_student_AD! --users
```


