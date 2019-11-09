# Ubuntu-setup

To use network proxy for updates

sudo -i 

ubuntu@ubuntu:~$ cat /etc/apt/apt.conf
Acquire::http::Proxy "http://Username:Password@proxy.foo.bar.edu.au:8080";
