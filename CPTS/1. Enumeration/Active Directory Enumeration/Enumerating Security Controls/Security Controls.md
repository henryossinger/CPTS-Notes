### Windows Defender: 
Get-MPComputerStatus - Shows the status of Defender 
- RealTimeProtectionEnabled = whether Defender is enabled 

### AppLocker: 
- Provides application Whitelisting on Windows environments 
- Orgs will commonly block items like Powershell, but only block 1 of Powershells default paths, or do not block Powershell ISE. 
```
Get-AppLockerPolicy -Effective | select -ExpandProperty RuleCollections
```

Check if Powershell is in Constrained Language mode, which will lock down many of Powershells default features (blocks COM objects, only allows approved .NET types, etc.)
```
$ExecutionContext.SessionState.LanguageMode
```

### LAPS 
Tool: LapsToolkit

Accounts that join computers to a domain receive the permissions "All Extended Rights" which has the ability to read LAPS password. These are good accounts to go after for enumeration.

```
Find-LAPSDelegatedGroups
``````
```
Find-AdmPwdExtendedRights
```
```
Get-LAPSComputers
```

