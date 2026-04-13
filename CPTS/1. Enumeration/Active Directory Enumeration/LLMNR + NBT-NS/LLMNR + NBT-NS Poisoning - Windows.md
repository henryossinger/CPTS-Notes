### Inveigh
- Similar to Responder, primarily for Windows hosts (written in Powershell and C#)

#### Inveigh Powershell Usage - 
import-module ./Inveigh.ps1
- Parameters: (get-command invoke-inveigh).Parameters
Invoke-Inveigh Y -NBNS Y -ConsoleOutput Y -FileOutput Y

#### Inveigh C# Usage -
- Inveigh must first be compiled before it can be ran as an executable. The Powershell version is no longer regularly updated 
- GET NTLMV2UNIQUE and GET NTLMV2USERNAMES will display captured hashes and usernames respectively.
- Press ESC to enter command mode 
- Once in command mode, type HELP to view all options to display 

