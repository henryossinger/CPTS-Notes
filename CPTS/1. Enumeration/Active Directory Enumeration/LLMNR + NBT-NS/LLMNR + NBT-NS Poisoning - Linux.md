**Man-in-the-Middle attacks on Link-Local Multicast Name Resolution (LLMNR) and NetBIOS Name Service (NBT-NS) broadcasts** 

These protocols are alternate methods of host identification when DNS fails (LLMNR first, then NBT if that also fails). When these protocols are used for resolution, ANY host is able to respond, hence the poisoning ability. Similar to ARP poisoning. 

LLMNR port - 5355
NBT-NS port - 137 

Primary Tool: **Responder / Inveigh**

## Attack Overview:
1. Host attempts to connect to print server \\print01.domain.local, mistypes the name for \\printer01.domain.local
2. DNS responds that the host is unknown
3. The host broadcasts asking if anyone knows the location of printer01.domain.local
4. Attacker responds stating that it is the host it is looking for (printer01.domain.local)
5. Host sends authentication request to the attacker with a username and NTLMv2 hash 
6. Hash can then be cracked offline / used for SMB relay attacks 

sudo responder -I <interface name> 

- pulls NTLM hashes if they are passed, saved in /usr/share/responders/logs 
- Hashes can then be cracked with hashcat or John 
	( hashcat -m <hash_type> <hash_file> <wordlist> )
		hashcat hash types: https://hashcat.net/wiki/doku.php?id=example_hashes
