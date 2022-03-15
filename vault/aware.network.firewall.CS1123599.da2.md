---
id: wnzi1lbss9hcrqqih86xc13
title: DA2
desc: DA2
updated: 1646159753013
created: 1645726814129
---
## Virtual IP(s)  
* [x]  
Name: VIP-F5-IPWeb-AWR1  
Interface: any  
Type: Static NAT  
External IP: 40.142.65.42 
Internal IP: 10.210.1.20 

## Address Group(s)  
* [x]  
Name: lhg_Web_AWR  
Members: Prod-Web-AWR01, Prod-Web-AWR02  

## Policy(s)
### ID: 538 n  
* [x]  
Name: AWR Clients  
Source: imperva-networks 
Destination: VIP-F5-IPWeb-AWR1  
Service: HTTPS, tcp_9090, tcp_9089  
NAT: Disabled  
Log: ALL  

### ID: 539 n  
* [x]  
Name: AWR Web to App  
Source: lhg_Web_AWR  
Destination: Prod-App-AWR01   
Service: HTTPS   
NAT: Disabled  
Log: ALL  

### ID: 476  
* [x]  
Name: MDS-SSRS Access  
Source: Prod-Web-RDUS01, **lhg_Web_AWR**  
Destination: Prod-App-SSRS01  
Service: HTTPS   
NAT: Disabled  
Log: ALL  

### ID: 540 n  
* [x]  
Name: AWR SSRS Access  
Source: Prod-App-AWR01  
Destination: Prod-App-SSRS01  
Service: HTTPS   
NAT: Disabled  
Log: ALL  

### ID: 378  
* [x]  
Name: Large FI (PG) SMB Access  
Source: lhg_App_IP_PG, **Prod-App-AWR01**  
Destination: Prod-FS-RD01  
Service: p_SMB   
NAT: Disabled  
Log: ALL  

### ID: 377
* [x]  
Name: Large FI (MDS) Apps to SQL   
Source: Prod-App-MTCA01, lhg_App_IP_PG, **Prod-App-AWR01**  
Destination: lhg_SQL_PG, lhg_SQL_20
Service: MS-SQL  
NAT: Disabled  
Log: ALL  
