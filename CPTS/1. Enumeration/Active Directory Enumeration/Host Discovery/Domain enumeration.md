### KEY DATA POINTS:
1. AD Users - enumerate valid accounts we can target 
2. AD Computers - Domain controllers, file servers, databases, etc. 
3. Services - Kerberos, NetBIOS, LDAP, DNS 
4. Vulnerable hosts and services - Anything for initial access / a quick win


##### Identifying Hosts: 
```
Wireshark / TCPDump 
Responder 
Fping (-asgq)
```
##### Enumerating Hosts: 
1. Nmap - (-oA) - enumerate services, OS, ports, etc. 
		Determine what the hosts are, what they are running, potential attack vectors. 

##### Identifying Users: 
1. Kerberute - user lists [here](https://github.com/insidetrust/statistically-likely-usernames)  - checks Kerberos pre-authentication failures, tends to not trigger logs / alerts 

#### Syntax:
```
kerbrute userenum -d INLANEFREIGHT.LOCAL --dc 172.16.5.5 jsmith.txt -o valid_ad_users
```
