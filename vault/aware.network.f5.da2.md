---
id: s2au8r52vzojqj4apr9hvgi
title: DA2
desc: ''
updated: 1645722299929
created: 1645721718925
---
## Node(s)
Name: Prod-Web-AWR01  
IP: 10.210.5.100  
Name: Prod-Web-AWR02  
IP: 10.210.5.101  

## Pool(s)  
Name: PL-IPWeb-AWR11  
Health Monitors: nodemonitor.html  
Members: Prod-Web-AWR01:443, Prod-Web-AWR02:443    
For other settings mirror PL-IPWeb-MAIN21  

Name: PL-IPWeb-AWR12  
Health Monitors: tcp  
Members: Prod-Web-AWR01:9090, Prod-Web-AWR02:9090   
For other settings mirror PL-IPWeb-MAIN22  

Name: PL-IPWeb-AWR13  
Health Monitors: tcp  
Members: Prod-Web-AWR01:9089,Prod-Web-AWR02:9089   
For other settings mirror PL-IPWeb-MAIN22  

## Virtual Server(s)
Name: VIP-IPWeb-AWR11  
Destination Address/Mask: 10.210.1.20  
Service Port: 443  
Default Pool: PL-IPWeb-AWR11  
Default Persistence Profile: cookie
For other settings mirror VIP-IPWeb-Main21  

Name: VIP-IPWeb-AWR12  
Destination Address/Mask: 10.210.1.20  
Service Port: 9090  
Default Pool: PL-IPWeb-AWR12  
Default Persistence Profile: cookie
For other settings mirror VIP-IPWeb-Main22   

Name: VIP-IPWeb-AWR13  
Destination Address/Mask: 10.210.1.20  
Service Port: 9089   
Default Pool: PL-IPWeb-AWR13  
Default Persistence Profile: cookie
For other settings mirror VIP-IPWeb-Main22  
