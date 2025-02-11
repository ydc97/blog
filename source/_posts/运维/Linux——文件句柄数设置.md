


---
### 背景

日常我们开发时，我们会遇到各种各样的奇奇怪怪的问题（踩坑o(╯□╰)o），这个常见问题系列就是我日常遇到的一些问题的记录文章系列，这里整理汇总后分享给大家，让其还在深坑中的小伙伴有绳索能爬出来。 同时在这里也欢迎大家把自己遇到的问题留言或私信给我，我看看其能否给大家解决。

### 开发环境

-   系统：Ubuntu

### 内容

在使用Linux时我们需要同时打开多个文件，来适配高并发的需求，这时就需要设置一下文件句柄数了，默认打开的是1024，下面是我们常用的命令：

ulimit 命令 1、查看当前打开文件句柄数量

```javascript
ulimit -n
```
2、查看所有配置参数

```javascript
ulimit -a 
```
3、临时修改句柄数

```javascript
unlimit -HSn 2048
```
4、永久修改句柄数

```javascript
sudo vim /etc/security/limits.conf
```

```javascript
#<domain> <type> <item> <value> 
# 
#* soft core 0 #root hard core 100000 
#* hard rss 10000 #@student hard nproc 20 #@faculty soft nproc 20 #@faculty hard nproc 50 #ftp hard nproc 0 #ftp - chroot /ftp 
#@student - maxlogins 4 
* soft nofile 65535 
* hard nofile 65535
```

5、设置全系统总限制

```javascript
sudo vim /etc/sysctl.conf
```

在底部追加
```javascript
fs.file-max=655350
```
立即生效
```javascript
sudo sysctl -p
```
这样就修改完毕了，用户级句柄数的修改需要重启一下才能生效，最好执行一下reboot，再次输入ulimit -n查看已经修改好了。

###### 本文声明：

本作品由 [cn華少](https://cloud.tencent.com/developer/tools/blog-entry?target=https%3A%2F%2Flinks.jianshu.com%2Fgo%3Fto%3Dwww.cnhuashao.com&source=article&objectId=1905523) 采用 [知识共享署名-非商业性使用 4.0 国际许可协议](https://cloud.tencent.com/developer/tools/blog-entry?target=https%3A%2F%2Flinks.jianshu.com%2Fgo%3Fto%3Dhttp%253A%252F%252Fcreativecommons.org%252Flicenses%252Fby-nc%252F4.0%252F&source=article&objectId=1905523) 进行许可。

本文参与 [腾讯云自媒体同步曝光计划](https://cloud.tencent.com/developer/support-plan)，分享自作者个人站点/博客。

原始发表：2021/11/14 ，如有侵权请联系 [cloudcommunity@tencent.com](mailto:cloudcommunity@tencent.com) 删除
