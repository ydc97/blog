

## 文件和目录操作[](https://muzing.top/posts/e800013b/#%E6%96%87%E4%BB%B6%E5%92%8C%E7%9B%AE%E5%BD%95%E6%93%8D%E4%BD%9C)

|常用命令|作用|
|---|---|
|cd <目录名>|进入某个目录|
|cd …|回上级目录|
|cd …/…|回上两级目录|
|cd ~|进入个人主目录|
|pwd|显示当前路径|
|ls|查看文件目录列表|
|ls -F|查看目录中内容（显示是文件还是目录）|
|ls -l|查看文件和目录的详细列表|
|ls -a|查看隐藏文件|
|ls -lh|查看文件和目录的详情列表（增强文件大小易读性）|
|ls -lSr|查看文件和目录列表（以文件大小升序查看）|
|tree|查看文件和目录的树形结构|
|mkdir <目录名>|创建目录|
|mkdir dir1 dir2|同时创建两个目录|
|mkdir -p /tmp/dir1/dir2|创建目录树|
|rm -f file1|删除 ‘file1’ 文件|
|rmdir dir1|删除 ‘dir1’ 目录|
|rm -rf dir1|删除 'dir1’目录及其内容|
|rm -rf dir1 dir2|同时删除两个目录及其内容|
|mv old_dir new_dir|重命名/移动目录|
|cp file1 file2|复制文件|
|cp dir/* .|复制某目录下的所有文件至当前目录|
|cp -a dir1 dir2|复制目录|
|cp -a /tmp/dir1 .|复制一个目录至当前目录|
|ln -s file1 link1|创建指向文件/目录的软链接|
|ln file1 link1|创建指向文件/目录的物理链接|
|find / -name file1|从根目录开始搜索文件/目录|
|find / -user user1|搜索用户user1的文件/目录|
|find /dir -name *.bin|在目录 /dir 中搜带有.bin后缀的文件|
|locate <关键词>|快速定位文件|
|locate *.mp4|寻找 .mp4 结尾的文件|
|whereis <关键词>|显示某二进制文件/可执行文件的路径|
|which <关键词>|查找系统目录下的某二进制文件|
|chmod ugo+rwx dir1|设置目录所有者(u)、群组(g)及其他人(o)的读®写(w)执行(x)权限|
|chmod go-rwx dir1|移除群组(g)与其他人(o)对目录的读写执行权限|
|chown user1 file1|改变文件的所有者属性|
|chown -R user1 dir1|改变目录的所有者属性|
|chgrp group1 file1|改变目录的所有者属性|
|chown user1:group1 file1|改变文件的所有人和群组|

## [](https://muzing.top/posts/e800013b/#%E6%96%87%E4%BB%B6%E6%9F%A5%E7%9C%8B%E5%92%8C%E5%A4%84%E7%90%86)文件查看和处理[](https://muzing.top/posts/e800013b/#%E6%96%87%E4%BB%B6%E6%9F%A5%E7%9C%8B%E5%92%8C%E5%A4%84%E7%90%86)

|常用命令|作用|
|---|---|
|cat file1|查看文件内容|
|cat -n file1|查看内容并标示行数|
|cat xxx.txt|awk ‘NR%2==1’|
|tac file1|从最后一行开始反看文件内容|
|more file1|查看一个长文件的内容|
|less file1|类似more命令，但允许反向操作|
|head -2 file1|查看文件前两行|
|tail -2 file1|查看文件的后两行|
|tail -f /log/msg|实时查看添加到文件中的内容|
|grep muzing hello.txt|在文件 hello.txt 中查找关键词 muzing|
|grep ^muzing hello.txt|在文件 hrllo.txt 中查找以muzing开头的内容|
|grep [0-9] hello.txt|选择 hello.txt 文件中所有包含数字的行|
|sed ‘s/s1/s2/g’ hello.txt|将 hello.txt 文件中的s1替换成s2|
|sed ‘/^$/d’ hello.txt|从 hello.txt 文件中删除所有空白行|
|sed ‘/ *#/d; /^$d’ hello.txt|从 hello.txt 文件中删除所有注释和空白行|
|sed -e ‘1d’ hello.txt|从文件 hello.txt 中排除第一行|
|sed -n ‘/s1/p’ hello.txt|查看只包含关键词"s1"的行|
|sed -e ‘s/ *$//’ hello.txt|删除每一行最后的空白字符|
|sed -e ‘s/s1//g’ hello.txt|从文档中只删除词汇s1并保留剩余全部|
|sed -n ‘1,5p;5q’ hello.txt|查看从第1行到第5行内容|
|sed -n ‘5p;5q’ hello.txt|查看第5行|
|paste file1 file2|合并两个文件或两栏的内容|
|paste -d ‘+’ file1 file2|合并两个文件或两栏的内容，中间用"+"区分|
|sort file1 file2|排序两个文件的内容|
|comm -1 file1 file2|比较两个文件的内容（去掉 ‘file1’ 所含内容）|
|comm -2 file1 file2|比较两个文件的内容（去掉 ‘file2’ 所含内容）|
|comm -3 file1 file2|比较两个文件的内容（去掉两文件共有部分）|

## [](https://muzing.top/posts/e800013b/#%E6%89%93%E5%8C%85%E5%92%8C%E8%A7%A3%E5%8E%8B)打包和解压[](https://muzing.top/posts/e800013b/#%E6%89%93%E5%8C%85%E5%92%8C%E8%A7%A3%E5%8E%8B)

| 常用命令                             | 作用             |
| -------------------------------- | -------------- |
| zip xxx.zip file                 | 压缩至zip包        |
| zip -r xxx.zip file1 file2 dir1  | 将多个文件+目录压成zip包 |
| unzip xxx.zip                    | 解压zip包         |
| tar -cvf xxx.tar file            | 创建非压缩tar包      |
| tar -cvf xxx.tar file1 fil2 dir1 | 将多个文件+目录打tar包  |
| tar -tf xxx.tar                  | 查看tar包的内容      |
| tar -xvf xxx.tar                 | 解压tar包         |
| tar -xvf xx.tar -C /dir          | 将tar包解压至指定目录   |
| tar -cvfj xxx.tar.bz2 dir        | 创建bz2压缩包       |
| tar -jxvf xxx.tar.bz2            | 解压bz2压缩包       |
| tar -cvfz xxx.tar.gz dir         | 创建gzip压缩包      |
| tar -zxvf xxx.tar.gz             | 解压gzip压缩包      |
| bunzip2 xxx.bz2                  | 解压bz2压缩包       |
| bzip2 filename                   | 压缩文件           |
| gunzip xxx.gz                    | 解压gzip压缩包      |
| gzip filename                    | 压缩文件           |
| gzip -9 filename                 | 最大程度压缩         |

## [](https://muzing.top/posts/e800013b/#%E5%85%B3%E6%9C%BA%E9%87%8D%E5%90%AF%E6%B3%A8%E9%94%80)关机/重启/注销[](https://muzing.top/posts/e800013b/#%E5%85%B3%E6%9C%BA%E9%87%8D%E5%90%AF%E6%B3%A8%E9%94%80)

|常用命令|作用|
|---|---|
|shutdown -h now|即可关机|
|shutdown -h 10|10分钟后关机|
|shutdown -h 11:00|11:00 关机|
|shutdown -h +10|预定时间关机（10分钟后）|
|shutdown -c|取消指定时间关机|
|shutdown -r now|重启|
|shutdown -r 10|10分钟之后重启|
|shutdown -r 11:00|定时重启|
|reboot|重启|
|init 6|重启|
|init 0|立刻关机|
|telinit|关机|
|poweroff|立刻关机|
|halt|关机|
|sync|buff数据同步到磁盘|
|logout|退出登录Shell|

## [](https://muzing.top/posts/e800013b/#%E7%B3%BB%E7%BB%9F%E4%BF%A1%E6%81%AF%E5%92%8C%E6%80%A7%E8%83%BD%E6%9F%A5%E7%9C%8B)系统信息和性能查看[](https://muzing.top/posts/e800013b/#%E7%B3%BB%E7%BB%9F%E4%BF%A1%E6%81%AF%E5%92%8C%E6%80%A7%E8%83%BD%E6%9F%A5%E7%9C%8B)

|常用命令|作用|
|---|---|
|uname -a|查看内核/OS/CPU信息|
|uname -r|查看内核版本|
|uname -m|查看处理器架构|
|arch|查看处理器架构|
|hostname|查看计算机名|
|who|显示当前登录系统的用户|
|who am i|显示登录时的用户名|
|whoami|显示当前用户名|
|cat /proc/version|查看linux版本信息|
|cat /proc/cpuinfo|查看CPU信息|
|cat /proc/interrupts|查看中断|
|cat /proc/loadavg|查看系统负载|
|uptime|查看系统运行时间、用户数、负载|
|env|查看系统的环境变量|
|lsusb -tv|查看系统USB设备信息|
|lspci -tv|查看系统PCI设备信息|
|lsmod|查看已加载的系统模块|
|grep MemTotal /proc/meminfo|查看内存容量|
|grep MemFree /proc/meminfo|查看空闲内存量|
|free -m|查看内存用量和交换区用量|
|date|显示系统日期时间|
|cal 2021|显示2021日历表|
|top|动态显示cpu/内存/进程等情况|
|vmstat 1 20|每1秒采一次系统状态，采20次|
|iostat|查看io读写/cpu使用情况|
|sar -u 1 10|查询cpu使用情况（1秒一次，共10次）|
|sar -d 1 10|查询磁盘性能|

## [](https://muzing.top/posts/e800013b/#%E7%A3%81%E7%9B%98%E5%92%8C%E5%88%86%E5%8C%BA)磁盘和分区[](https://muzing.top/posts/e800013b/#%E7%A3%81%E7%9B%98%E5%92%8C%E5%88%86%E5%8C%BA)

|常用命令|作用|
|---|---|
|fdisk -l|查看所有磁盘分区|
|swapon -s|查看所有交换分区|
|df -h|查看磁盘使用情况及挂载点|
|df -hl|查看磁盘使用情况及挂载点|
|du -sk * \| sort -rn|从高到低依次显示文件和目录大小|
|mount /dev/hda2 /mnt/hda2|挂载had2盘|
|mount -t ntfs /dev/sdc1 /mnt/usbhd1|指定文件系统类型挂载（如ntfs）|
|mount -o loop xxx.iso /mnt/cdrom|挂载iso文件|
|mount /dev/sda1 /mnt/usbdisk|挂载usb盘/闪存设备|
|umount -v /dev/sda1|通过设备名卸载|
|umount -v /mnt/mymnt|通过挂载点卸载|
|fuser -km /mnt/hda1|强制卸载（慎用）|

## [](https://muzing.top/posts/e800013b/#%E7%94%A8%E6%88%B7%E5%92%8C%E7%94%A8%E6%88%B7%E7%BB%84)用户和用户组[](https://muzing.top/posts/e800013b/#%E7%94%A8%E6%88%B7%E5%92%8C%E7%94%A8%E6%88%B7%E7%BB%84)

|常用命令|作用|
|---|---|
|useradd muzing|创建用户|
|userdel -r muzing|删除用户|
|usermod -g group_name user_name|修改用户的组|
|usermod -aG group_name user_name|将用户添加到组|
|usermod -s /bin/ksh -d /home/codepig -g dev muzing|修改用户 muzing 的登陆Shell、主目录以及用户组|
|groups test|查看 test 用户所在的组|
|groupadd group_name|创建用户组|
|groupdel group_name|删除用户组|
|groupmod -n new_name old_name|重命名用户组|
|su - user_name|完整切换到一个用户环境|
|passwd|修改密码|
|passwd muzing|修改某用户的密码|
|w|查看活动用户|
|id muzing|查看指定用户 muzing 信息|
|last|查看用户登录日志|
|crontab -l|查看当前用户的计划任务|
|cut -d: -f1 /etc/passwd|查看系统所有用户|
|cut -d: -f1 /etc/group|查看系统所有组|

## [](https://muzing.top/posts/e800013b/#%E7%BD%91%E7%BB%9C%E5%92%8C%E8%BF%9B%E7%A8%8B%E7%AE%A1%E7%90%86)网络和进程管理[](https://muzing.top/posts/e800013b/#%E7%BD%91%E7%BB%9C%E5%92%8C%E8%BF%9B%E7%A8%8B%E7%AE%A1%E7%90%86)

## [](https://muzing.top/posts/e800013b/#%E5%B8%B8%E8%A7%81%E7%B3%BB%E7%BB%9F%E6%9C%8D%E5%8A%A1%E5%91%BD%E4%BB%A4)常见系统服务命令[](https://muzing.top/posts/e800013b/#%E5%B8%B8%E8%A7%81%E7%B3%BB%E7%BB%9F%E6%9C%8D%E5%8A%A1%E5%91%BD%E4%BB%A4)

|常用命令|作用|
|---|---|
|chkconfig --list|列出系统服务|
|service <服务名> status|查看某个服务|
|service <服务名> start|启动某个服务|
|service <服务名> stop|终止某个服务|
|service <服务名> restart|重启某个服务|
|systemctl status <服务名>|查看某个服务|
|systemctl start <服务名>|启动某个服务|
|systemctl stop <服务名>|终止某个服务|
|systemctl restart <服务名>|重启某个服务|
|systemctl enable <服务名>|开启自启动|
|systemctl disable <服务名>|关闭自启动|

## [](https://muzing.top/posts/e800013b/#dpkg%E5%8C%85%E7%AE%A1%E7%90%86%E5%91%BD%E4%BB%A4)DPKG包管理命令[](https://muzing.top/posts/e800013b/#dpkg%E5%8C%85%E7%AE%A1%E7%90%86%E5%91%BD%E4%BB%A4)

|常用命令|作用|
|---|---|
|dpkg -c xxx.deb|列出deb包的内容|
|dpkg -i xxx.deb|安装/更新deb包|
|dpkg -r pkg_name|移除deb包|
|dpkg -P pkg_name|移除deb包（不保留配置）|
|dpkg -l|查看系统中已安装deb包|
|dpkg -l pkg_name|显示包的大致信息|
|dpkg -L pkg_name|查看deb包安装的文件|
|dpkg -s pkg_name|查看包的详细信息|
|dpkg -unpack xxx.deb|解开deb包的内容|

## [](https://muzing.top/posts/e800013b/#apt%E8%BD%AF%E4%BB%B6%E5%B7%A5%E5%85%B7)APT软件工具[](https://muzing.top/posts/e800013b/#apt%E8%BD%AF%E4%BB%B6%E5%B7%A5%E5%85%B7)

|常用命令|作用|
|---|---|
|apt-cache search pkg_name|搜索程序包|
|apt-cache show pkg_name|获取包的概览信息|
|apt-get install pkg_name|安装/升级软件包|
|apt-get purge pkg_name|卸载软件（包括配置）|
|apt-get remove pkg_name|卸载软件（不包括配置）|
|apt-get update|更新包索引信息|
|apt-get upgrade|更新已安装软件包|
|apt-get clean|清理缓存|

## [](https://muzing.top/posts/e800013b/#rpm-%E5%8C%85%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7)RPM 包管理工具[](https://muzing.top/posts/e800013b/#rpm-%E5%8C%85%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7)

|常用命令|作用|
|---|---|
|rpm -qa|查看已安装的rpm包|
|rpm -q pkg_name|查询某个rpm包|
|rpm -q --whatprovides xxx|显示xxx功能是由哪个包提供的|
|rpm -q --whatrequires xxx|显示xxx功能被哪个程序包依赖的|
|rpm -q --changelog xxx|显示xxx包的更改记录|
|rpm -qi pkg_name|查看一个包的详细信息|
|rpm -qd pkg_name|查询一个包所提供的文档|
|rpm -qc pkg_name|查看已安装rpm包提供的配置文件|
|rpm -ql pkg_name|查看一个包安装了哪些文件|
|rpm -qf filename|查看某个文件属于哪个包|
|rpm -qR pkg_name|查询包的依赖关系|
|rpm -ivh xxx.rpm|安装rpm包|
|rpm -ivh --test xxx.rpm|测试安装rpm包|
|rpm -ivh --nodeps xxx.rpm|安装rpm包时忽略依赖关系|
|rpm -e xxx.rpm|卸载程序包|
|rpm -Fvh pkg_name|升级确定已安装的rpm包|
|rpm -Uvh pkg_name|升级rpm包（若未安装则会安装）|
|rpm -V pkg_name|RPM包详细信息校验|

## [](https://muzing.top/posts/e800013b/#yum%E5%8C%85%E7%AE%A1%E7%90%86%E5%91%BD%E4%BB%A4)YUM包管理命令[](https://muzing.top/posts/e800013b/#yum%E5%8C%85%E7%AE%A1%E7%90%86%E5%91%BD%E4%BB%A4)

|常用命令|作用|
|---|---|
|yum repolist enabled|显示可用的源仓库|
|yum search pkg_name|搜索软件包|
|yum install pkg_name|下载并安装软件包|
|yum install --downloadonly pkg_name|只下载不安装|
|yum list|显示所有程序包|
|yum list installed|查看当前系统已安装包|
|yum list updates|查看可以更新的包列表|
|yum check-update|查看可升级的软件包|
|yum update|更新所有软件包|
|yum update pkg_name|升级指定软件包|
|yum deplist pkg_name|列出软件包依赖关系|
|yum remove pkg_name|删除软件包|
|yum clean all|清除缓存|
|yum clean packages|清除缓存的软件包|
|yum clean headers|清除缓存的header|