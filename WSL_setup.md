# WSL2 Ubuntu 20.04 LTS setup guide
This is a step-by-step guide to configure Ubuntu through WSL.  
The contents are:  
1. Windows preparation for WSL 2
2. Installation and updates of WSL 2 (Ubuntu 20.04)
3. Initial setup for Ubuntu environment
4. Installation of Microsoft terminal
5. Setup of Microsoft terminal



## 1. Installation of WSL

 ### A. Windows features on or off (via GUI & Command-line method)  

   A.1 (GUI) Open Windows features on or off   
   A.2 (GUI) Check the **| Virtual Machine Platform |** and **| Windows Subsystem for Linux |** options and restart (as **required**)  

A.1 (Command-line) Open Powershell  
A.2 (Command-line) Enter these two command in the Powershell  
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

### B. WSL 2 preparation
  #### B.1 Download and install WSL 2 kernel (https://aka.ms/wsl2kernel)
  #### B.2 Set WSL 2 as default: Run `wsl --set-dafault-version 2` in Powershell

### C. Download Linux distribution (Ubuntu 20.04 LTS)
#### b.1 Open **Microsoft Store** 
#### b.2 Search **Ubuntu 20.04 LTS** and Click Install (~500 MB of download).  
*Note 1: At the time of writing, Ubuntu 20.04 is the latest version.*  
*Note 2: This setup guide is tested for Ubuntu specifically but "might" also work with other distributions (i.e. Kali and CentOS) with some changes to syntax.*  

### c. Install Ubuntu 20.04 LTS

#### c.1 Launch Ubuntu 20.04 LTS (First time)
#### c.2 Enter new UNIX username and password

### d. WSL and WSL2 Manipulation

*Note: WSL is just a compatability/translater layer while WSL 2 has a kernel. TLDR: WSL = fake linux, WSL 2 = real linux. *
