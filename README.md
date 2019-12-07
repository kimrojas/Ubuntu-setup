# Ubuntu-setup

To use network proxy for updates

sudo -i 

ubuntu@ubuntu:~$ cat /etc/apt/apt.conf
Acquire::http::Proxy "http://Username:Password@proxy.foo.bar.edu.au:8080";

https://www.youtube.com/watch?v=oyNjjzg-UXo



vm tools: apt install open-vm-tools-desktop

## 1. Install essential programs
```
apt update
apt upgrade

apt install open-vm-tools-desktop

apt install vim
apt install ssh
apt install xcrysden 

```
Restart VMware

## 2. (Optional) Transfer ssh key from an already working computer

copy ~/.ssh (old computer) to ~/.ssh (new computer)

```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/*
ssh-add
```
