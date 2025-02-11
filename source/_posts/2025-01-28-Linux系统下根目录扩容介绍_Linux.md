---
title: Linux系统下根目录扩容介绍
date: 2025-01-18 13:55
update: 2025-01-18 13:55
---


1、查看Linux磁盘情况

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/202112170833301.png)

**lsblk**命令 用于列出所有可用块设备的信息，并且显示他们之间的依赖关系。

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/202112170833302.png)

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/202112170833303.png)

新建磁盘分区

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/202112170833314.png)

更改新分区磁盘类型

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/202112170833315.png)

保存分区操作并重启操作系统

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/202112170833316.png)

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/202112170833327.png)

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/202112170833328.png)

格式化分区

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/202112170833329.png)

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/2021121708333210.png)

创建新的物理卷

#pvcreate命令 用于将物理硬盘分区初始化为物理卷，以便LVM使用。

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/2021121708333211.png)

查看 lvm 卷组信息

#vgdisplay命令 用于显示LVM卷组的信息。如果不指定”卷组”参数，则分别显示所有卷组的属性

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/2021121708333312.png)

向卷组添加物理卷

<table><tbody><tr><td><p>1</p></td><td><div><p><code>vgextend </code><code>/dev/mapper/vg--maycur</code> <code>/dev/vda3</code></p></div></td></tr></tbody></table>

  
#通过 df -h 查看所需添加到的卷组 名称无须加root

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/2021121708333313.png)

开始扩容

<table><tbody><tr><td><p>1</p></td><td><div><p><code>lvextend -L +49G </code><code>/dev/mapper/vg--maycur-root</code> <code>/dev/vda3</code></p></div></td></tr></tbody></table>

#lvextend命令 用于在线扩展逻辑卷的空间大小，而不中断应用程序对逻辑卷的访问

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/2021121708333314.png)

同步文件系统

<table><tbody><tr><td><p>1</p></td><td><div><p><code>xfs_growfs </code><code>/dev/mapper/vg--maycur-root</code></p></div></td></tr></tbody></table>

![在这里插入图片描述](https://img.jbzj.com/file_images/article/202112/2021121708333315.png)

到此这篇关于Linux系统下根目录扩容介绍的文章就介绍到这了,更多相关Linux根目录扩容内容请搜索脚本之家以前的文章或继续浏览下面的相关文章希望大家以后多多支持脚本之家！

原文链接：https://blog.csdn.net/qq\_41580613/article/details/121962728

本文来自互联网用户投稿，该文观点仅代表作者本人，不代表本站立场。本站仅提供信息存储空间服务，不拥有所有权，不承担相关法律责任。  
如若内容造成侵权/违法违规/事实不符，请将相关资料发送至 reterry123@163.com 进行投诉反馈，一经查实，立即处理！
