# ADPhoneListUpdate

import-module ActiveDirectory

#Get all users with telephone numbers

$users = Get-ADUser -LDAPFilter "(telephoneNumber=*)" -Properties sAMAccountName, telephoneNumber

#check lenth of telephone numbers

$data = ForEach ($User In $Users)

 

{

 

    $name = $User.sAMAcountName

 

    $Phone = $User.telephoneNumber

 

    If ($Phone.length -gt 8 ) {write-output $user | select name, telephoneNumber | Sort-Object name }

 

}

$data | Export-Csv -Path C:\Users\itadmin11\Desktop\PhoneList\Long\LongPhoneNumber.csv -NoTypeInformation
