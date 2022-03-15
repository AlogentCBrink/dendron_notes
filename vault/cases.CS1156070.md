---
id: nnugw0hc6g4mljc2c0hep2p
title: CS1156070
desc: NXT SkyOne Images
updated: 1646946949909
created: 1646934073593
---
### Description:  
Firewall update for NXT SkyOne images.  
### Note:
```
Please create a new Firewall Object in NSH and DA2:
NAME: rh_echeck.skyone.org 
FQDN: echeck.skyone.org 

Please create a new Firewall Service in NSH and DA2:
NAME: tcp_7572
DETAILS: TCP/7572

Please create a new Firewall Policy in NSH And DA2:
ID: new  
NAME: NXT SkyOne Images  
FROM: CATApp   
SOURCE: CAT-NXT-SKONE, CAT-APP-NXT02 
TO: outside 
DESTINATION: rh_echeck.skyone.org   
SERVICE: tcp_7572
NAT: Enabled
SECURITY PROFILES: 
- AV: Default
- IPS: Default
- SSL: certificate-inspection
LOG: All
```
### Opened: 
03/10/2022
### Completed: 
03/10/2022
