---
id: pgUXitG0La3rm1ClXqIvA
title: CS1092574
desc: 'New firewall object creation'
updated: 1645727998843
created: 1644507203599
---
### Description:  
Create new firewall objects for Prod-Web-AWR01/02 and Prod-App-AWR01  
^description
```
in NSH:
Please remove object Prod-DM-IP01 from lhg_App_IP_Main
Please rename object Prod-DM-IP01 (10.110.6.100) to Prod-App-AWR01
Please create two new objects:
Prod-Web-AWR01 (10.110.5.100)
Prod-Web-AWR02 (10.110.5.101)
Please then update Policy 98, and add both Prod-Web-AWR01 and Prod-Web-AWR02 to the Source list

===
In DA2:
Please rename object Prod-DM-IP01 (10.210.6.100) to Prod-App-AWR01
Please create two new objects:
Prod-Web-AWR01 (10.210.5.100)
Prod-Web-AWR02 (10.210.5.101)
Please update Policy 98, and add both Prod-Web-AWR01 and Prod-Web-AWR02 to the Source list
```
### Opened: 
02/08/2022  
### Completed: 
02/08/2022 

