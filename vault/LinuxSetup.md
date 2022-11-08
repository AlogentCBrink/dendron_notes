---
id: qr2eipil5rdtbnwhpmv5f42
title: Linux Setup
desc: ''
updated: 1646345488356
created: 1646326200696
---
## Download Distribution and Install (Ubuntu 20.04)  
```Powershell
Invoke-WebRequest -Uri https://aka.ms/wslubuntu2004 -OutFile Ubuntu.appx -UseBasicParsing  
Rename-Item ./Ubuntu.appx ./Ubuntu.zip
Expand-Archive ./Ubuntu.zip ./Ubuntu
cd .\Ubuntu\
.\ubuntu.exe
```

## Config Linux  

### Date/Time in History
```bash
vim ~/.bashrc

add HISTTIMEFORMAT="%Y-%m-%d %T "
```

### Install updates  
```bash
sudo apt update
sudo apt upgrade
```

### Install Starship  
![[LinuxSetup.starship#^inst_star]]

### Symbolic link "repos"  
```bash
ln -s /mnt/c/Brinks\ Stuff/repos/ repos
cd repos #<== to test#
```

### SSH Config  
![[LinuxSetup.ssh#^config_ssh]]  

### Docker install




