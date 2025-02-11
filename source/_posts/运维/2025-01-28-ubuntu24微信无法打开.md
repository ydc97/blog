


默认开启了AppArmor，会导致类似qq等程序无法启动。用下面的命令可以临时关闭，或者添加到配置文件保存。

sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0

- 永久生效
    
    `sudo vim /etc/sysctl.conf` 
    
- 加上一行
    
    `kernel.apparmor_restrict_unprivileged_userns=0`