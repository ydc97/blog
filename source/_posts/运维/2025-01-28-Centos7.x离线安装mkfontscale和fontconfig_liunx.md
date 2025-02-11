



---
### 1 在线安装方式

```bash
yum install -y mkfontscale

yum install -y fontconfig

fc-list

fc-list :lang=zh
```

###   
2 离线安装方式

2.1 [安装r](https://so.csdn.net/so/search?q=%E5%AE%89%E8%A3%85r&spm=1001.2101.3001.7020)pm文件

链接: https://pan.baidu.com/s/1s9tUzRvse0uniRkiukbAOw?pwd=m1qy

提取码: m1qy  
 

2.2 执行安装命令

```bash
rpm -ivh ./*.rpm --nodeps --force  #我的是当前目录，所以是./
```

2.3进入 fonts 目录

```bash
cd /usr/share/fonts
```

上传[字体文件](https://so.csdn.net/so/search?q=%E5%AD%97%E4%BD%93%E6%96%87%E4%BB%B6&spm=1001.2101.3001.7020)到 /usr/share/fonts下（可以将windows环境下的字体复制到linux系统下，但是部分字体存在不兼容的情况）

2.4 更改字体的执行权限

```bash
chmod -R 755 /usr/share/fonts/*
```

然后刷新配置

```bash
mkfontscale

mkfontdir

fc-cache

fc-list
```

最后重启服务
