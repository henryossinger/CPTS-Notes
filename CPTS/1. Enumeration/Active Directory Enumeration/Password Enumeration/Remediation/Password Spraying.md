## Detection
- Monitor for Event ID 4625: An account failed to login - and 4771: Kerberos pre-authentication failed
- Lots of these logs in a short timeframe indicates spraying
- Logs with usernames that do not exist indicate spraying

## Mitigation
- MFA 
- Restricting Access 
- Password Hygenie 
- Reduce impact if accounts are breached (Privilege of least trust)
  
Research on remediation / detection: https://www.hub.trimarcsecurity.com/post/trimarc-research-detecting-password-spraying-with-security-event-auditing