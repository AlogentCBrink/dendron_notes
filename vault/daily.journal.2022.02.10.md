---
id: tA9OUtOmPW06rNdMLYsU1
title: '2022-02-10'
desc: ''
updated: 1644528583989
created: 1644511464334
traitIds:
  - journalNote
---
## AWARE Documentation  
## LFI Reports not running
Prod-SQL-N20\SQL20  
Tested email via powershell successfully.  
No email profiles configured for Alogent.  
Created email account `Alogent SMTP Server` and profile `Alogent Notifications`
Test email received.
Ran SQL Server Agent job and received report.
Setup meeting w/ Matt and Philip to do Prod-SQL-N21\SQL20 tomorrow (02/11/2022)
## SQL Reports email setup Cluster 1 (SF#1905)
Configured and tested db_mail.  
Copied SQL Server Agent Jobs and disabled them in DA2.  
### SQL-ECM1.alogentcloud.local
PROD-SQL06\ECM1  
DR-SQL-N03\INS2  
Configured db_mail on DR-SQL-N03\INS2 and replicated jobs:
1. [SQL-ECM1] Monthly Item Counts for Susan - BRINK

### SQL-IP1.alogentcloud.local (SQL-IP1)
PROD-SQL01\IP1  
DR-SQL-N01\INS1  
Configured db_mail on DR-SQL-N01\INS1 and replicated jobs:
1. [BPSLicensing] Licensing Billing Data Report - Monthly
2. [BPSLicensing] Licensing Billing Data Report - Quarterly
3. [BPSLicensing] On Prem Monthly Counts - BRINK
4. [IPHub Main2] Monthly Purge Report - BRINK
5. [SQL-IP1] Bpslicensing Monthly Purge - BRINK
6. [SQL-IP1] Monthly Item Counts for Lee - BRINK
7. IPHubMain2 - Create and Cleanup SQL Partitions  

Removed jobs from DR-SQL-N01\INS1:
1. [SQL-IP1] IPA Monthly Counts - BRINK

### SQL-IP1.alogentcloud.local (SQL-IP2)
PROD-SQL01\IP1  
DR-SQL-N03\INS1  
Configured db_mail on DR-SQL-N03\INS1 and replicated jobs:
1. [IPHub Main1] Monthly Purge Report - Brink
2. [MitekUsage] Mitek Billing Data Report - Monthly
3. [SQL-IP1] Monthly Item Counts for Susan - BRINK
4. [SQL-IP1] Viso Mitek Report
5. [SQL-IP2] Main Mitek Purge History - BRINK
6. [SQL-IP2] Main Mitek Purge Temp Images - BRINK
7. [SQL-IP2] Main Mitek Purge Transactions - BRINK
8. [SQL-IP2] Main Mitek Purge Usage - BRINK
9. Check21 - Create and Cleanup SQL Partitions

Removed jobs from PROD-SQL01\IP1:
1. [SQL-IP2] Main1 Central CU of Florida Reset Trigger - SARAH
2. [SQL-IP2] Main1 Fraud Check - SARAH
3. [SQL-IP2] Main1 Via Reset Trigger - SARAH