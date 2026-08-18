# MS Teams bulk phone-numbers assignment
PowerShell Script to Bulk Assign Phone Numbers in Microsoft Teams
```powershell

Clear

$CSV = Import-Csv -Path "C:\Users\asusvc66admin\Documents\telephone-loop.csv"

$i = 0;

ForEach ($Row in $CSV) {

                    Write-Host "Working with $($Row.'UPN')" 

                    $UPN_RAM = $($Row.'UPN');
                    $Number_RAM = $($Row.'Number');
                    $Ext_RAM = $($Row.'Ext');
                    $Clerid_RAM = $($Row.'Clerid');
                    $OLVRPolicy_RAM = $($Row.'OLVRPolicy');

                    Set-CsPhoneNumberAssignment -Identity $UPN_RAM -PhoneNumber "+1$Number_RAM;ext=$Ext_RAM" -PhoneNumberType DirectRouting
                    #Set-CsPhoneNumberAssignment -Identity $UPN_RAM -PhoneNumber "+1$Number_RAM" -PhoneNumberType DirectRouting
					#Write-Host "EV and HVM Enabled" -ForegroundColor Yellow -BackgroundColor DarkGreen
                    Write-Host "Phone Number Assigned" -ForegroundColor Yellow -BackgroundColor DarkGreen
                    
                    #Grant-CsCallingLineIdentity -Identity $UPN_RAM -PolicyName $Clerid_RAM
					#Write-Host "Caller ID Policy Assigned" -ForegroundColor Yellow -BackgroundColor DarkGreen
                    
                    Grant-CsOnLineVoiceRoutingPolicy -Identity $UPN_RAM -PolicyName $OLVRPolicy_RAM
					Write-Host "VR Policy Assigned" -ForegroundColor Yellow -BackgroundColor DarkGreen
                    
                    $i += +1;

                    Write-Host "$i Users have been processed.."
                    Write-Host ""

}



#Write-Host "Generating Report..."

   #Get-CsOnLineUser | Select UserPrincipalName, EnterpriseVoiceEnabled, OnPremLineURI, CallingLineIdentity, OnLineVoiceRoutingPolicy | Export-Csv -Path C:\Users\asusvc66admin\Documents\loop-report.csv -Notype

#Write-Host "Report generated"



```
# CSV file example
<img width="645" height="316" alt="image" src="https://github.com/user-attachments/assets/fa35096b-6216-47dc-9236-d24972fd10b1" /></b>
# Plain TXT view
<img width="504" height="201" alt="image" src="https://github.com/user-attachments/assets/1fb58d49-f970-46f7-97b5-f7dbe3531358" />

