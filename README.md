# Ubuntu-setup

## Pre-setup

### Install Vmware with ubuntu (or other OS)

See guide:

https://www.youtube.com/watch?v=oyNjjzg-UXo


### To use network proxy for updates

sudo -i 

ubuntu@ubuntu:~$ cat /etc/apt/apt.conf.d/proxy.conf
```
Acquire::http::Proxy "http://Username:Password@proxy.foo.bar.edu.au:8080";
```

Ref: https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-set-the-proxy-for-apt-for-ubuntu-18-04/

## 1. Install essential programs
```
apt update
apt upgrade

sudo apt-get install ubuntu-restricted-extras
apt install vim
apt install xcrysden 
apt install htop
```
** Mouse wheel for VIM **
add to ` set mouse=a` /etc/vim/vimrc  
ref: https://stackoverflow.com/questions/40576522/enable-vi-mouse-wheel-scrolling-using-bash-on-ubuntu-on-windows-10/40715383


**Optional for VMware**
```
apt install open-vm-tools-desktop
```
Restart VMware

## 2. ssh configurations 

Install ssh
`apt install ssh`

### Create ssh keys

Note: This assumes that there are no previously generated ssh key, if there are please back it up. \
(Location of keys = ~/.ssh )

```
ssh-keygen -t rsa -C "your_email@example.com"
```

Reference: https://confluence.atlassian.com/bitbucketserver/creating-ssh-keys-776639788.html

### (Optional) Transfer ssh key from an already working computer

copy ~/.ssh (old computer) to ~/.ssh (new computer)

```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/*
ssh-add
```

### Add ssh key to cluster

copy the contents of `~/.ssh/id_rsa.pub` to `(cluster):~/.ssh/authorized_keys`



