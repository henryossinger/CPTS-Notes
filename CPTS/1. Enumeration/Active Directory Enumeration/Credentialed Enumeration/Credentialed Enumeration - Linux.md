Steps for further enumeration once we have credentials to the domain: 
Enumerate the following: 
- Users
- Groups
- Determine who is of interest 

### CrackMapExec (NetExec)
Can enumerate the following: 
- 

<CrackMapExec (Protocol) -h --- Displays the help for the selected protocol>

User Enum: 
- sudo crackmapexec smb <DC-IP> -u <user> -p <pass> --users 

Group Enum:
	sudo crackmapexec smb <DC-IP> -u <user> -p <pass> --groups

#### DETERMINE WHICH GROUPS ARE OF INTEREST: Admins, Domain Admins, Executives, etc.

Logged On Users: 
	sudo crackmapexec smb <DC-IP> -u <user> -p <pass> --loggedon-users

Share Searching: 
Useful to see what shares are available, and if we have any permissions to them 
- sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --shares


#### NetExec Modules: 
Spider Plus: Digs through network shares and pulls information 
```
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 -M spider_plus --share 'Department Shares'
```

## SMB Enumeration:

Tools: SMBMap

Recursively look through SMB shares (the option --dir-only specifies directories)
```
smbmap -u forend -p Klmcargo2 -d INLANEFREIGHT.LOCAL -H 172.16.5.5 -R 'Department Shares' --dir-only
```

### IMPACKET

psexec.py: 
Clone of psexec from SysInternals suite with slightly more features 
- Can upload a service executable that is able to provide remote functionality. Able to create an interactive session running as the SYSTEM
- psexec requires local admin privileges on the system to run 
```
psexec.py inlanefreight.local/wley:'transporter@4'@172.16.5.125
```

wmiexec.py 
- semi-interactive session that sends commands through WMI 
- Does not drop file or executables, stealthier than psexec
 ```
wmiexec.py inlanefreight.local/wley:'transporter@4'@172.16.5.5
```

## Windapsearch 
- Utilizes LDAP queries for enumeration 
- Able to enumerate domain admins and Privileged Users recursively (-PU checks nested group memberships which can be easily missed by admins)
```
python3 windapsearch.py --dc-ip 172.16.5.5 -u forend@inlanefreight.local -p Klmcargo2 --da
```
# ENDED OFF AT BLOODHOUND.py 




