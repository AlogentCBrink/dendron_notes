---
id: pbcegn83d7s7sn4jztyz58h
title: '2022-03-08'
desc: ''
updated: 1646775781445
created: 1646755065315
traitIds:
  - journalNote
---
### TODO:
* [x] Prod Aware Documentation   
* [X] SQL Job Update for Lee  
* [X] TAM Access to FIS Import folders
* [ ] Monitoring Staging  
* [ ] F5 move for Dominic  
* [ ] SQL Jobs Documentation  
* [ ] Tenable AWS  
* [ ] FG Alerting  
 
# Prod Aware Documentation 
[SF0000732](https://alogent.lightning.force.com/lightning/r/DC_Request__c/a751S0000008VBXQA2/view)   
Re-updated ticket  

# SQL Job Update for Lee
[SF00001951](https://alogent.lightning.force.com/lightning/r/DC_Request__c/a751S0000008XBKQA2/view)  
Updated job to only include the requested 10 fields.  Commented out the rest incase changes are needed.  
Tested both changes.  

Mitek US (Prod-SQL01\IP1) 
- Replicated to DS-SQL-N03/INS01  
  
Mitek CA  (PROD-SQL-N20/SQL20)
- Replicated to PROD-SQL-N21/SQL20 and DS-SQL-N20/SQL20  

# TAM Access to FIS Import folders  
[SF00001928](https://alogent.lightning.force.com/lightning/r/DC_Request__c/a751S0000008WqRQAU/view)  
## AD Group:
Shared Folder - Monitor Alerts  
## Members:  

| Current           | Requested         |
| ----------------- | ----------------- |
| Alfredo Noriega   |                   |
| Christopher Henry | Christopher Henry |
| Davonte Hearnton  | Davonte Hearnton  |
| Jamar Washington  | Leanna Chisholm   |
| Jeremy Simmons    | Jeremy Simmons    |
| Leanna Chisholm   | Leanna Chisholm   |
| Melissa Skaar     |                   |
| Mitchell Odell    | Mitch Odell       |
| Roberto Nunez     | Christopher Henry |
| Sarah Anderson    |                   |
| Seth Ward         | Seth Ward         |
| Triston Fuel      | Triston Fuel      |

## Server List:

| HostName        | RecordData  | Completed      |
| --------------- | ----------- | -------------- |
| Prod-App-AVT01  | 10.110.9.20 | Yes            |
| Prod-App-CABC01 | 10.110.9.27 | Yes            |
| Prod-App-CCF01  | 10.110.9.10 | Yes            |
| Prod-App-CLRP01 | 10.110.9.34 | Yes            |
| Prod-App-COOP01 | 10.110.9.31 | Yes            |
| Prod-App-CTCU01 | 10.110.9.28 | Yes            |
| Prod-App-CUCO01 | 10.110.9.29 | yes            |
| Prod-App-CUCO02 | 10.110.9.36 | Failed (WRM)   |
| Prod-App-CUOH01 | 10.110.9.15 | Yes            |
| Prod-App-DFCU01 | 10.110.9.11 | Yes            |
| Prod-App-EFCU01 | 10.110.9.24 | Yes            |
| Prod-App-ETCU01 | 10.110.9.25 | Yes            |
| Prod-App-FBF02  | 10.110.9.39 | Yes            |
| Prod-App-FSCU01 | 10.110.9.21 | Yes            |
| Prod-App-HACU01 | 10.110.9.37 | Yes            |
| Prod-App-LEO01  | 10.110.9.38 | Yes            |
| Prod-App-LFCU01 | 10.110.9.12 | Yes            |
| Prod-App-LVCU01 | 10.110.9.13 | Yes            |
| Prod-App-MAMF01 | 10.110.9.22 | Yes            |
| Prod-App-MFF01  | 10.110.9.17 | Yes            |
| Prod-App-PFCU01 | 10.110.9.30 | Failed (WRM)   |
| Prod-App-PRIN01 | 10.110.9.32 | Yes            |
| Prod-App-RIVE01 | 10.110.9.40 | Failed (Share) |
| Prod-App-SFCU01 | 10.110.9.18 | Yes            |
| Prod-App-STCF01 | 10.110.9.23 | Yes            |
| Prod-App-SWFC01 | 10.110.9.35 | Yes            |
| Prod-App-TAUN01 | 10.110.9.36 | Failed (Share) |
| Prod-App-TFCU01 | 10.110.9.33 | Yes            |
| Prod-App-TNF01  | 10.110.9.14 | Yes            |
| Prod-App-UECU01 | 10.110.9.19 | Yes            |
| Prod-App-WFCU01 | 10.110.9.26 | Yes            |

## Created Script
```Powershell
foreach ($hostname in $computers) {
   $fqdname = $hostname + ".alogentcloud.local"
   echo $fqdname
   Invoke-Command -ComputerName $fqdname -Credential $mycreds -ScriptBlock { 
      $path = (Get-SmbShare -Name "FIS_Input").Path
      echo Before
      (Get-ACL -Path $path).Access | Format-Table IdentityReference,FileSystemRights,AccessControlType,IsInherited,InheritanceFlags -AutoSize
      $ACL = Get-ACL -Path $path
      $AccessRule = New-Object System.Security.AccessControl.FileSystemAccessRule("ALOGENTCLOUD\Shared Folder - Monitor Alerts","Modify","ContainerInherit, ObjectInherit","None","Allow")
      $ACL.SetAccessRule($AccessRule)
      $ACL | Set-Acl -Path $path 
      echo After    
      (Get-ACL -Path $path).Access | Format-Table IdentityReference,FileSystemRights,AccessControlType,IsInherited,InheritanceFlags -AutoSize
   }
}
```