# WSL 2 setup guide (Ubuntu 20.04 LTS) 
This is a step-by-step guide to configure Ubuntu through WSL.  
The contents are:  
1. Windows preparation for WSL 2
2. Installation and updates of WSL 2 (Ubuntu 20.04)
3. Initial setup for Ubuntu environment
4. Installation of Microsoft terminal
5. Setup of Microsoft terminal



## 1. Installation of WSL

#### A. Windows features on or off (via GUI & Command-line method)  

+ A.1 (GUI) Open Windows features on or off   
+ A.2 (GUI) Check the **| Virtual Machine Platform |** and **| Windows Subsystem for Linux |** options and restart (as **required**)  

+ A.1 (Command-line) Open Powershell  
+ A.2 (Command-line) Enter these two command in the Powershell  
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

#### B. WSL 2 preparation
+ B.1 Download and install WSL 2 kernel (https://aka.ms/wsl2kernel)
+ B.2 Set WSL 2 as default: In powershell, run:    
```
wsl --set-default-version 2
```

#### C. Download Linux distribution (Ubuntu 20.04 LTS)
+ C.1 Open **Microsoft Store** 
+ C.2 Search **Ubuntu 20.04 LTS** and Click Install (~500 MB of download).  

*Note 1: At the time of writing, Ubuntu 20.04 is the latest version.*  
*Note 2: This setup guide is tested for Ubuntu specifically but "might" also work with other distributions (i.e. Kali and CentOS) with some changes to syntax.*  

#### D. Install Ubuntu 20.04 LTS
+ D.1 Launch Ubuntu 20.04 LTS (First time)  
+ D.2 Enter new UNIX username and password  
+ D.3 Verification: In powershell, run:
```
wsl --list --verbose
```

*OUTPUT*  
```
  NAME            STATE           VERSION
* Ubuntu-20.04    Running         2
```

> INSTALLATION DONE! ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## 2. Initial Ubuntu setup

#### A. Updates
+ Open Ubuntu terminal (*From here terminal = Ubuntu terminal)
+ Run:  `sudo apt update && sudo apt -y upgrade`



References
- https://docs.microsoft.com/en-us/windows/wsl/install-win10#install-your-linux-distribution-of-choice  
- https://docs.microsoft.com/en-us/windows/wsl/wsl2-kernel

