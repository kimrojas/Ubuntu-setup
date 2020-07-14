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
    `MaterialsDark (preferred), DraculaPlus, Afterglow, Andromeda, Dark+, Elementary, Espresso, Firewatch, Liquidcarbon, Lovelace, MonokaiRemastered, Jetbrains Darcula, Brogrammer`
+ B.2 Click on `Get theme` (which will copy the code to your clipboard)
+ B.3 Open settings.json again (`Ctrl + ,`) and find the line `"schemes": [],`
+ B.4 Paste the code in between the `[]`. It should look like this:
```
    "schemes": [
{
  "name": "MaterialDark",
  "black": "#212121",
  "red": "#b7141f",
  "green": "#457b24",
  "yellow": "#f6981e",
  "blue": "#134eb2",
  "purple": "#560088",
  "cyan": "#0e717c",
  "white": "#efefef",
  "brightBlack": "#424242",
  "brightRed": "#e83b3f",
  "brightGreen": "#7aba3a",
  "brightYellow": "#ffea2e",
  "brightBlue": "#54a4f3",
  "brightPurple": "#aa4dbc",
  "brightCyan": "#26bbd1",
  "brightWhite": "#d9d9d9",
  "background": "#232322",
  "foreground": "#e5e5e5"
}
],
```
+ B.5 Add the line `"colorScheme": "MaterialDark",` above the `"source": "Windows.Terminal.Wsl"`
+ B.6 The font colors should be changed now. 

#### C. Change font
+ C.1 Go to fonts.google.com and download `Roboto Mono` (Get the Regular 400 option)
+ C.2 Unzip and double click the .ttf file and Install
+ C.3 In settings.json (Ubuntu section). add the lines above `"source": "Windows.Terminal.Wsl"`:
```
"fontFace": "Roboto Mono",
"fontSize": 11, 
```

## 2. Initial Ubuntu setup

#### A. Updates
+ A.1 Open Ubuntu terminal (*From here terminal = Ubuntu terminal)
+ A.2 Run:  `sudo apt update && sudo apt -y upgrade`
+ A.3 Initial VIM setup: Follow https://github.com/sickill/vim-monokai Instructions
+ A.3 (Alternative) https://github.com/crusoexia/vim-monokai
*Note: my ~/.vimrc is in the folder for you to check*

#### B. Enable GUI

+ B.1 Add the following to `~/.bashrc`: `export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0
+ B.2 On windows setup an Xserver by following this video: https://www.youtube.com/watch?v=uL8nnuvybL8
*Note: I also have a comment there regarding basic troubleshooting. TLDR: Make firewall exception for xserver and turn off native opengl*
+ B.3 Restart Terminal

#### C. Install a essential apps (some with GUI)

+ C.1 Run this command
```
sudo apt install ssh openssh-server openssh-client gedit firefox xcrysden
```
+ C.2 Run a test app. Enter `gedit` in terminal... it should umm  be gedit.
*Note: I use this theme for gedit: http://en.leoiannacone.com/2014/12/monokai-theme-for-gedit-gtksourceview/ *

#### D. Setting up python
I am not fond of installing apps globally unless its too much of a hassle. In this section, I will locally install miniconda (as python) and pycharm (as editor)

+ D.1 Make an apps folder  
`mkdir ~/apps && cd ~/apps`
+ D.2 Download miniconda installer using:  
`wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`
*Note: Latest version is 3.7 as of the moment, change the link as needed in the future*
+ D.3 Install Miniconda:  
`chmod +x Miniconda3-latest-Linux-x86_64.sh && ./Miniconda3-latest-Linux-x86_64.sh`
*Note 1: Read license (and agree to terms), and change installation location to `~/apps/miniconda3`*
*Note 2: On "Do you want to initialize Miniconda 3 ...?" -> type yes *
+ D.4 Turn off initiate conda on startup by running:
`echo "conda config --set auto_activate_base false" > ~/.condarc`


### Issue/s

Setting default user for imported distro:   
+ tldr = make /etc/wsl.conf 
+ https://github.com/microsoft/WSL/issues/3974



References
- https://docs.microsoft.com/en-us/windows/wsl/install-win10#install-your-linux-distribution-of-choice  
- https://docs.microsoft.com/en-us/windows/wsl/wsl2-kernel

