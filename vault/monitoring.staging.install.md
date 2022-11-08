---
id: pzc5223c08t6w7g1fji8jqk
title: Install
desc: ''
updated: 1646414784883
created: 1646409139271
---
[Youtube - Install Zabbix Server(2019)](https://www.youtube.com/watch?v=yYmkFf3AEBo)

## Install Postgress SQL  
https://www.postgresql.org/download/linux/ubuntu/  
1. `sudo sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'`  
2. `sudo wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -`
3. `sudo apt-get update`
4. `sudo apt install postgresql`
   
## Install Zabbix Software
   https://www.zabbix.com/download?zabbix=6.0&os_distribution=ubuntu&os_version=20.04_focal&db=postgresql&ws=apache  

2. `wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.0-1+ubuntu20.04_all.deb`
3. `sudo dpkg -i zabbix-release_6.0-1+ubuntu20.04_all.deb`
4. `sudo apt update`
5. `sudo apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent`
6. `sudo -u postgres createuser --pwprompt zabbix`
<!-- $$unflow3r -->
1. `sudo -u postgres createdb -O zabbix zabbix`
2. `zcat /usr/share/doc/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix`
3. `sudo vim /etc/zabbix/zabbix_server.conf`  
   DBPassword=password  
1. `sudo systemctl restart zabbix-server zabbix-agent apache2`
2. `sudo systemctl enable zabbix-server zabbix-agent apache2`
1. `service zabbix-server start`  
3. http://10.90.3.20/zabbix  

## Configure Frontend
   https://www.zabbix.com/documentation/6.0/en/manual/installation/frontend  
1. Follow wizard
1. Change password  
<!-- $$unflow3r -->  

https://www.zabbix.com/documentation/6.0/en/manual/quickstart/login  
1. add user: Chris, Judit

https://www.zabbix.com/documentation/6.0/en/manual/discovery/auto_registration
1. setup auto registration.  
2. 



## Agent (Client) Install
https://www.zabbix.com/documentation/6.0/en/manual/installation/install_from_packages/win_msi  

Windows, amd64, 6.0, OpenSSL, MSI    
https://www.zabbix.com/download_agents?version=6.0+LTS&release=6.0.1&os=Windows&os_version=Any&hardware=amd64&encryption=OpenSSL&packaging=MSI&show_legacy=0

### Agent 1
***ST-App-LIC01***
1. run MSI.  


### Agent 2
***ST-App-Main21***
1. run MSI.  
2. 