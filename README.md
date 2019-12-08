# Ubuntu-setup

## Pre-setup

### Install Vmware with ubuntu (or other OS)

See guide:

https://www.youtube.com/watch?v=oyNjjzg-UXo


### To use network proxy for updates

sudo -i 

ubuntu@ubuntu:~$ cat /etc/apt/apt.conf
```
Acquire::http::Proxy "http://Username:Password@proxy.foo.bar.edu.au:8080";
```


## 1. Install essential programs
```
apt update
apt upgrade

apt install vim
apt install ssh
apt install xcrysden 
apt install htop
```

**Optional for VMware**
```
apt install open-vm-tools-desktop
```
Restart VMware

## 2. (Optional) Transfer ssh key from an already working computer

copy ~/.ssh (old computer) to ~/.ssh (new computer)

```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/*
ssh-add
```
