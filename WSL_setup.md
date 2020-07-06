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

## 2. (Optional) Windows terminal installation and setup
I personally don't like the limited features of the default Ubuntu terminal. It has no tabs and less customization but this one has more features. In this section, I explain how to install windows terminal and give a simple setup to polish the user interface (color, themes, etc.).

#### A. Install windows terminal
+ A.1 Open Micrsoft store
+ A.2 Install **Windows Terminal**
+ A.3 Open Terminal (from now on Windows terminal = terminal)
+ A.4 Press `Ctrl + , ` or **Settings** from the drop down menu to open Settings.json (open with any editor)
+ A.5 Change default profile from Powershell to Ubuntu
  - Go to the section with `"name": "Ubuntu-20.04",`
  - Copy the *guid* (the item enclosed by "{ }"
  - Paste the guid of Ubuntu to the item in `"defaultProfile".`
  - This will change the initial shell to be Ubuntu rather than the former Powershell
  - Save (`Ctrl + s` or depens on your editor)
  - Close the file and Terminal
  - Re-open the Terminal and check if Ubuntu is the first tab to show... It should.

#### B. Choose Theme
+ B.1 Go to https://atomcorp.github.io/themes/ and choose theme. Recommended themes are:  
    `DraculaPlus (prefer), Afterglow, Andromeda, Dark+, Elementary, Espresso, Firewatch, Liquidcarbon, Lovelace, MaterialsDarker, MonokaiRemastered, Jetbrains Darcula, Brogrammer`


## 2. Initial Ubuntu setup

#### A. Updates
+ Open Ubuntu terminal (*From here terminal = Ubuntu terminal)
+ Run:  `sudo apt update && sudo apt -y upgrade`



References
- https://docs.microsoft.com/en-us/windows/wsl/install-win10#install-your-linux-distribution-of-choice  
- https://docs.microsoft.com/en-us/windows/wsl/wsl2-kernel

