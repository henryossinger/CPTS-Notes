### CrackMapExec (NetExec)
- CrackMapExec (Protocol) -h --- Displays the help for the selected protocol

User Enum: 
- sudo crackmapexec smb <DC-IP> -u <user> -p <pass> --users 

Group Enum:
	sudo crackmapexec smb <DC-IP> -u <user> -p <pass> --groups

# DETERMINE WHICH GROUPS ARE OF INTEREST: Admins, Domain Admins, Executives, etc.

Logged On Users: 
	sudo crackmapexec smb <DC-IP> -u <user> -p <pass> --loggedon-users 

## LEFT OFF AT (CME SHARE SEARCHING) SECTION