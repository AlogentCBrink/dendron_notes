---
id: e7y8ci6s4w1ld8t1zlwfe5c
title: SF00001905
desc: SQL Script Audit
updated: 1647370034884
created: 1647366887163
---
## Link:
[00001905](https://alogent.lightning.force.com/lightning/r/DC_Request__c/a751S0000008Wj1QAE/view)  

## Description:  
```
We need to audit the SQL Server Agent Jobs in DA2 for both Cluster 1 and Cluster 2 to ensure that all Jobs are replicated in case of a failover.
```
## Notes:
### 03/15/2022
```
Worked on documentation standardization.  
```
### 02/10/2022
```
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

#### SQL-ECM1.alogentcloud.local
* PROD-SQL06\ECM1  
* DR-SQL-N03\INS2  
Configured db_mail on DR-SQL-N03\INS2 and replicated job [SQL-ECM1] Monthly Item Counts for Susan - BRINK
```
  
## Opened: 
02/10/2022   
## Completed:

