# PowerShell
Scripts
#Identify deleted users, recover, and confirm recovery#
Get-ADObject -filter {Deleted -eq $True -and ObjectClass -eq "user"} -includeDeletedObjects
Restore-ADObject -Identity '[user GUID]'
Get-ADObject -Filter 'Name -like "*[user name]*"' -Properties *| select-object Name, sAMAccountName, memberOf, IsDeleted|Format-List
