---
id: qKSAaNaHcyYkHfYjHHhM7
title: Aware Production Env Buildout
desc: 'Aware Production Env Buildout'
updated: 1646753238234
created: 1644506367350
---

[SF#00001732](https://alogent.lightning.force.com/lightning/r/DC_Request__c/a751S0000008VBXQA2/view)  

## Aware Environment SF1732 | CS1123599 

### External URL:
**AWARE.alogentcloud.com**  
This website is behind the Web Application Firewall (WAF) with the default security policies.  The default policies include geo-blocking of "High Risk" countries.  
***We will need a list of IPs, per client to whitelist and allow access to the application***  

### Service Account:
![[aware.accounts]]

### Web Load Balancer:
F5-IPWeb-AWR11  
* NSH IP: 10.110.1.20  
* DA2 IP: 10.210.1.20  

### Web Server:
Prod-Web-AWR01  
* NSH IP: 10.110.5.100  
* DA2 IP: 10.210.5.100  

### Application Server:
Prod-App-AWR01  
* NSH IP: 10.110.6.100  
* DA2 IP: 10.210.6.100  

### SMB File Share:
\\\Prod-FS-RD01.alogentcloud.local\AWARE  

### Database Instance:
SQL-21.alogentcloud.local  



