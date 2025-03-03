---
title: "Eshead查询格式化 es head查询数据_jkfox的技术博客_51CTO博客"
source: "https://blog.51cto.com/u_13479/10451601"
date: "2025-03-03T14:41:47+08:00"
update: "2025-03-03T14:41:47+08:00"
tags:
  - "Linux"
categories: "运维"
---
**文章目录**

- 1.elasticsearch-head界面说明
- 2.索引的创建
- 3.索引的删除
- 4.索引数据查看
- 5.索引文档的增删改查操作（restful风格）
- Rest风格操作
- 5.1.添加索引(创建数据库)
- 5.2.数据类型那么name这个字段用不用指定类型呢。毕竟我们关系型数据库是需要指定类型的啊！ 字符串类型text、 keyword 数值类型long, integer, short, byte, double, float, half float, scaled float 日期类型date 布尔值类型boolean 二进制类型binary
- 5.3.指定字段的类型（创建索引）
- 5.3.1默认字段类型(7以后的版本可以不指定类型可以用\_doc表示默认类型)
- 5.4.修改操作
- 5.4.1直接put覆盖原数据(缺点：如果数据没写全就会丢失)
- 5.4.2使用update
- 5.5.删除操作
- 5.6.对文档的基本操作
- 5.6.1获取数据GET
- 5.6.2简单的条件查询
- 5.6.3复杂查询

有想备考软考的小伙伴吗？0基础担心考不过，科目太多不知道怎么选？关注我，我整理了我一个多月考过高级的软考备考攻略，可以直接免费领取。

 [https://d.51cto.com/eDOcp1](https://d.51cto.com/eDOcp1)

## 1.elasticsearch-head界面说明

在浏览器访问[http](https://rk.51cto.com/download?cateId=&cid=&tid=90&utm_platform=pc&utm_medium=51cto&utm_source=blog&utm_content=rksyzq_blog#http)://IP:9100即可访问

![Eshead查询格式化 es head查询数据_elasticsearch](https://s2.51cto.com/images/blog/202404/09111658_6614b32a1b80086047.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

可以看到我们的elasticsearch-head正是连接了我们的ES:9200地址，并且，ES集群名称为my-es，集群健康值为green，ES集群下有一个节点，名称为node-1

**集群健康值的几种状态如下：**

　绿色：最健康的状态，代表所有的分片包括备份都可用

　黄色：基本的分片可用，但是备份不可用（也可能是没有备份）

　红色：部分的分片可用，表明分片有一部分损坏。此时执行查询部分数据仍然可以查到，遇到这种情况，还是赶快解决比较好

   灰色：未连接到elasticsearch服务

通过上图我们可以看到有三个索引(.开头的名称)，但是这三个索引不是我们自己创建的，接下来，我们将自己创建索引来对其进行更好地了解

## 2.索引的创建

创建一个test\_index1的索引

![Eshead查询格式化 es head查询数据_数据_02](https://s2.51cto.com/images/blog/202404/09111658_6614b32a2d5c884431.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

创建完成后，在首页即可查看到我们的索引，0-4代表着我们的5个分片数

![Eshead查询格式化 es head查询数据_数据_03](https://s2.51cto.com/images/blog/202404/09111658_6614b32a4933871020.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

## 3.索引的删除

![Eshead查询格式化 es head查询数据_学习_04](https://s2.51cto.com/images/blog/202404/09111658_6614b32a7939267070.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

## 4.索引数据查看

在数据浏览中可以查看到我们各个索引的数据

![Eshead查询格式化 es head查询数据_elasticsearch_05](https://s2.51cto.com/images/blog/202404/09111658_6614b32a8b1ec31447.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

## 5.索引文档的增删改查操作（restful风格）

###      Rest风格操作

![Eshead查询格式化 es head查询数据_elasticsearch_06](https://s2.51cto.com/images/blog/202404/09111658_6614b32aa8a6114027.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

### 5.1.添加索引(创建数据库)

在kibana中使用restful风格新建索引(库)

【工具可以自由选择，不限定一定要使用kibana】

![Eshead查询格式化 es head查询数据_数据_07](https://s2.51cto.com/images/blog/202404/09111658_6614b32ac32f785791.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

### 5.2.数据类型  
那么name这个字段用不用指定类型呢。毕竟我们关系型数据库是需要指定类型的啊！  
字符串类型text、 keyword  
数值类型long, integer, short, byte, double, float, half float, scaled float  
日期类型date  
布尔值类型boolean  
二进制类型binary

### 5.3.指定字段的类型（创建索引）

#### 5.3.1默认字段类型(7以后的版本可以不指定类型可以用\_doc表示默认类型) 

![Eshead查询格式化 es head查询数据_elasticsearch_08](https://s2.51cto.com/images/blog/202404/09111658_6614b32ad6b9639460.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184)

###  5.4.修改操作

#### 5.4.1直接put覆盖原数据(缺点：如果数据没写全就会丢失)

#### 5.4.2使用update 

###  5.5.删除操作

###  5.6.对文档的基本操作

#### 5.6.1获取数据GET

#### 5.6.2简单的条件查询 

![Eshead查询格式化 es head查询数据_elasticsearch_09](https://s2.51cto.com/images/blog/202404/09111658_6614b32af1dbf24896.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184 "在这里插入图片描述")

#### 5.6.3复杂查询

**5.6.3.1条件查询** 

**5.6.3.2结果过滤**

 **5.6.3.3排序**

   **5.6.3.4分页查询**

   **5.6.3.5与或非查询(布尔值查询)**

    **5.6.3.6过滤查询(大于小于查询)**

    **5.6.3.7匹配条件查询(多个条件用空格分开)**

    **5.6.3.8精确查询**

     **5.6.3.9高亮查询**

![Eshead查询格式化 es head查询数据_Eshead查询格式化_10](https://s2.51cto.com/images/blog/202404/09111659_6614b32b1c43155921.png?x-oss-process=image/watermark,size_16,text_QDUxQ1RP5Y2a5a6i,color_FFFFFF,t_30,g_se,x_10,y_10,shadow_20,type_ZmFuZ3poZW5naGVpdGk=/format,webp/resize,m_fixed,w_1184 "在这里插入图片描述")

      **5.6.3.10自定义高亮条件**

有想备考软考的小伙伴吗？0基础担心考不过，科目太多不知道怎么选？关注我，我整理了我一个多月考过高级的软考备考攻略，可以直接免费领取。

 [https://d.51cto.com/eDOcp1](https://d.51cto.com/eDOcp1)

本文章为转载内容，我们尊重原作者对文章享有的著作权。如有内容错误或侵权问题，欢迎原作者联系我们进行内容更正或删除文章。

- **赞**
- **收藏**
- **评论**
- **举报**

**相关文章**

[![](https://s2.51cto.com/wyfs02/M02/75/BB/wKioL1ZBnI-B9Wp6AAAYCuI5xOA885_middle.jpg?x-oss-process=image/format,webp/ignore-error,1)](https://blog.51cto.com/u_13479)

- 239.6万

人气

- 6

评论

- 25

收藏

**近期文章**

- [1.2025年3月DAMA-CDGA/CDGP数据治理认证报名，大家都来](https://blog.51cto.com/hbcx/13449350 "2025年3月DAMA-CDGA/CDGP数据治理认证报名，大家都来")
- [2.明达云网关：钢铁行业煤气排水器的智能守护者](https://blog.51cto.com/u_16880992/13449148 "明达云网关：钢铁行业煤气排水器的智能守护者")
- [3.山东2025年上半年软考报名流程是怎样的？](https://blog.51cto.com/u_15131005/13449385 "山东2025年上半年软考报名流程是怎样的？")
- [4.ST7735S](https://blog.51cto.com/u_15950621/13448875 "ST7735S")
- [5.金蝶予力全球伙伴，“AI+管理”共创世界一流生态！](https://blog.51cto.com/u_15675284/13449359 "金蝶予力全球伙伴，“AI+管理”共创世界一流生态！")

[![新人福利](https://s2.51cto.com/images/100/base/empty.png?x-oss-process=image/format,webp/ignore-error,1)](https://blog.51cto.com/activity-first-publish#xiang)

**文章目录**

- 1.elasticsearch-head界面说明
- 2.索引的创建
- 3.索引的删除
- 4.索引数据查看
- 5.索引文档的增删改查操作（restful风格）
- Rest风格操作
- 5.1.添加索引(创建数据库)
- 5.2.数据类型那么name这个字段用不用指定类型呢。毕竟我们关系型数据库是需要指定类型的啊！ 字符串类型text、 keyword 数值类型long, integer, short, byte, double, float, half float, scaled float 日期类型date 布尔值类型boolean 二进制类型binary
- 5.3.指定字段的类型（创建索引）
- 5.3.1默认字段类型(7以后的版本可以不指定类型可以用\_doc表示默认类型)
- 5.4.修改操作
- 5.4.1直接put覆盖原数据(缺点：如果数据没写全就会丢失)
- 5.4.2使用update
- 5.5.删除操作
- 5.6.对文档的基本操作
- 5.6.1获取数据GET
- 5.6.2简单的条件查询
- 5.6.3复杂查询