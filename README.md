# MS Teams bulk phone-numbers assignment
PowerShell Script to Bulk Assign Phone Numbers in Microsoft Teams
```powershell
2
Connect-MicrosoftTeams
3
 
4
Import-Csv ".\users.csv" | ForEach-Object {
5
Set-CsPhoneNumberAssignment `
6
-Identity $_.UserPrincipalName `
7
-PhoneNumber $_.PhoneNumber `
8
-PhoneNumberType DirectRouting
9
}
10
```
