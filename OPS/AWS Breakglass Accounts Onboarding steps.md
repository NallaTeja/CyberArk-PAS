User give info about aws account like below example:-
~~~
{
"AccountNumberAddress": "123456789012"
"BreakglassPW": "1^UZRBLaknakdv7jbvakZ"
"BreakglassReconAccessKeyID": "AKIA5ankjvnsakjFX"
"BreakglassReconAccessSecret": "lkjafnka;knl/kajlvankfdalkndcokfd"
"BreakglassReconUserName" : "ENGINEER_P_RECON"
"BreakglassUserName" : "ENGINEER_P_BREAKGLASS"
"RootConsoleEmail" : "XYZ-PQR-ENGINEER-P@EMAIL.COM"
"RootConsoleMFASecret" : "35G3SGJLBFLFNSOKGKDFNGLSKNIN753AFDKNSCMLKASDLFCOISNLKFCO78CNK"
"RootConsolePW" : "Qs^osfmncs0ncskjnfoln"
}
~~~

## Onboard AWS Break Glass and Reconcilation Accounts

1. log into the pvwa UI with your credentials and go to "Additional details & actions in classic interface"
2. Select "Add Account"
3. Select safe - AWS Break Glass Prod / Non-Prod to store the account
4. Select Device type as 'Cloud Service'
5. Select platform - 'AWS-Break GLass'
6. Enter AWS account/VPC address in address field
   i.e., Eg: **123456789012**
7. Select the box beside 'username' and 
   i.e., Eg: **ENGINEER_P_BREAKGLASS**
8. paste the password of the break-glass account in password fields
    i.e., Eg: **1^UZRBLaknakdv7jbvakZ**
9. click 'save'

## Onboard AWS Reconciliation account

1. User logs into PAM and clicks on Accounts view (Classic UI) under accounts in left pane
2. Select "Add Account"
3. Select safe - 'AWS-IAM-Recon' to store the account
4.  Select Device type as 'Cloud Service'
5.  Select platform - 'AWS-AccessKeys'
6.  Enter AWS IAM username and AWS Acess key ID
   i.e., Eg: **ENGINEER_P_RECON** & **AKIA5ankjvnsakjFX**
7. Enter AWS Access Key Secret
   i.e., Eg: **lkjafnka;knl/kajlvankfdalkndcokfd** 
8. click 'save'
9. At the top righ side corner in search bar type break glass username (ENGINEER_P_BREAKGLASS)
10. Select that account & click Reconcile Account 'Associate'
11. Type the BreakglassReconUserName (ENGINEER_P_RECON) slect the account and click associate.

## Onboard AWS Root accounts
1. User logs into PAM and clicks on Accounts view (Classic UI) under accounts in left pane
2. Select "Add Account"
3. Select safe - AWS Root Prod / Non-Prod to store the account
4.  Select Device type as 'Cloud Service'
5.  Select platform - 'AWS-ROOT'
6. Enter AWS account/VPC address in address field
   i.e., Eg: **123456789012**
7. Enter root console MFA secret in MFA field
    i.e., Eg: **35G3SGJLBFLFNSOKGKDFNGLSKNIN753AFDKNSCMLKASDLFCOISNLKFCO78CNK**
8. Select the box beside 'username' and enter root console EMail
   i.e., Eg: **XYZ-PQR-ENGINEER-P@EMAIL.COM**
9. paste the password of the root console account in password fields
    i.e., Eg: **Qs^osfmncs0ncskjnfoln**
10. click 'save'

