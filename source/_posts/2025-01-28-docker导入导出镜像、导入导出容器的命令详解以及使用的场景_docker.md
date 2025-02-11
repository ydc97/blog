---
title: docker导入导出镜像、导入导出容器的命令详解以及使用的场景_docker
date: 2020-01-18 13:55
update: 2020-01-18 13:55
tags: Linux
categories: 运维
---

---
#### 文章目录

-   [一、Docker 提供用于管理镜像和容器命令](https://blog.csdn.net/weixin_45876175/article/details/130909849#Docker__9)
-   -   [导出镜像（docker save）与导入镜像（docker load）：](https://blog.csdn.net/weixin_45876175/article/details/130909849#docker_savedocker_load_10)
    -   [导出容器（docker export）与导入容器（docker import）：](https://blog.csdn.net/weixin_45876175/article/details/130909849#docker_exportdocker_import_18)
-   [二、四个命令的用法和应用场景](https://blog.csdn.net/weixin_45876175/article/details/130909849#_30)
-   -   [1.案例一](https://blog.csdn.net/weixin_45876175/article/details/130909849#1_31)
    -   [2.案例二](https://blog.csdn.net/weixin_45876175/article/details/130909849#2_39)
-   [二、四个命令的参数解析](https://blog.csdn.net/weixin_45876175/article/details/130909849#_48)
-   -   [1.docker save 命令：](https://blog.csdn.net/weixin_45876175/article/details/130909849#1docker_save__49)
    -   [2.docker load 命令：](https://blog.csdn.net/weixin_45876175/article/details/130909849#2docker_load__53)
    -   [3.docker export 命令：](https://blog.csdn.net/weixin_45876175/article/details/130909849#3docker_export__58)
    -   [4.docker import 命令：](https://blog.csdn.net/weixin_45876175/article/details/130909849#4docker_import__62)

___

## 一、[Docker](https://so.csdn.net/so/search?q=Docker&spm=1001.2101.3001.7020) 提供用于管理镜像和容器命令

### 导出镜像（docker save）与导入镜像（docker load）：

这是一对操作，用于处理 Docker 镜像。这个操作会将所有的镜像层以及元数据打包到一个 tar 文件中。然后，你可以使用 docker load 命令将这个 tar 文件导入到任何 Docker 环境中。例如：

```c
导出：docker save -o <保存路径>/myimage.tar myimage:latest 导入：docker load -i <路径>/myimage.tar
```

这种方式主要用于分享或迁移整个镜像，包括所有版本、标签和历史。

### 导出容器（docker export）与导入容器（docker import）：

这也是一对操作，用于处理 Docker 容器。docker export 命令可以将运行中的容器的文件系统导出为一个 tar 文件。然后，你可以使用 docker import 命令将这个 tar 文件作为一个新的镜像导入。例如：

```c
导出：docker export <容器ID> > mycontainer.tar 导入：docker import mycontainer.tar
```

这种方式主要用于分享或迁移容器的当前状态。这不包括容器的历史或元数据，如环境变量，所以它常常用于对容器进行快照。

**`总的来说，如果你想要保存整个镜像，包括它的所有历史和标签，那么你应该使用 docker save 和 docker load命令。而如果你只是想要保存一个容器的当前状态，那么你应该使用 docker export 和 docker import 命令。`**

## 二、四个命令的用法和应用场景

### 1.案例一

假设你在你的开发环境中创建了一个新的 Docker 镜像，这个镜像包含了你的应用和所有依赖项，你已经测试了这个镜像，并且打了一个标签，称其为 “myapp:1.0”。现在你想要将这个镜像移到生产环境。这个场景中，你应该使用 docker save 和 docker load 命令。具体操作如下：

在开发环境中，你运行 docker save -o myapp\_1.0.tar myapp:1.0。这将创建一个名为 “myapp\_1.0.tar” 的 tar 文件，其中包含了 “myapp:1.0” 镜像的所有层和元数据。  
你可以将这个 tar 文件复制到你的生产环境，然后在那里运行 docker load -i myapp\_1.0.tar。这将导入 “myapp:1.0” 镜像，你可以立即在生产环境中使用它。

### 2.案例二

假设你在容器中运行了一个复杂的数据分析任务，这个任务运行了几个小时后产生了一些结果。你想要保存这个容器的当前状态，以便稍后可以从这个点继续。在这个场景中，你应该使用 docker export 和 docker import 命令。具体操作如下：

你运行 docker export mycontainer > mycontainer.tar，这将创建一个 tar 文件，其中包含了 “mycontainer” 的文件系统。  
然后，你可以使用 docker import mycontainer.tar myanalysis:snapshot1 命令，创建一个新的镜像，这个镜像包含了你的容器在任务运行时的状态。你可以在稍后恢复这个镜像，继续你的数据分析任务。  
**`请注意，docker export 和 docker import 命令不会保存或恢复容器的历史或元数据，如环境变量。因此，它们更适合于保存和恢复容器的“快照”，而不是用于迁移或分享镜像。`**

## 二、四个命令的参数解析

### 1.docker save 命令：

\-o 参数表示输出的文件路径和名称，后面紧跟着要保存的镜像名称。例如，docker save -o /path/to/save/myimage.tar myimage:tag

### 2.docker load 命令：

\-i 参数表示输入的文件路径和名称。例如，docker load -i /path/to/load/myimage.tar

### 3.docker export 命令：

docker export 命令后直接跟容器的 ID 或名称。例如，docker export mycontainer > /path/to/save/mycontainer.tar

### 4.docker import 命令：

docker import 的参数包括输入的文件路径和名称，以及新镜像的名称和标签。例如，docker import /path/to/import/mycontainer.tar newimage:tag

**`注意：在 docker save 和 docker load 的操作中，你在操作镜像，镜像名称后可以带标签（如果不指定标签，默认为 latest）。而在 docker export 和 docker import 的操作中，你在操作容器（对应的是一个容器的 ID 或名称）和镜像（可以指定新的镜像名称和标签）。`**
