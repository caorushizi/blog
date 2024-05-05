---
title: "编程必备基础： 计算机组成原理、操作系统、计算机网络"
seoTitle: "计算机基础知识"
seoDescription: "Learn about the essential basics of programming: computer architecture, operating systems, and computer networks"
datePublished: Mon Apr 29 2024 11:32:57 GMT+0000 (Coordinated Universal Time)
cuid: clvkvrlpw000208ju6mysckhb
slug: 57yw56il5bf5ash5z656ga77yaioiuoeeulacuue7hoaikowoneqhuoageatjes9noezue7noageiuoeeulacuue9kee7na
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/n8Qb1ZAkK88/upload/9378fbcc0a46c108e62e7460d3a95baa.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1714830291175/5e8d60e2-3e3a-4b42-989a-9ec522705cec.webp

---

# 计算机发展历史

### 计算机发展简史

1. 1946年： 电子管计算机
    
2. 1957年： 晶体管计算机
    
3. 1964年：集成电路计算机
    
4. 1980年： 超大规模集成电路计算机
    

### 第一阶段计算机

第二次世界大战是电子管计算机产生的催化剂（解密德国海军的密文）

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714385008608/e04bc2de-cca5-4aa9-8ca4-befb3a895557.png align="center")

* 集成度小，空间占用大
    
* 功耗幔，运行速度慢
    
* 操作复杂，切换程序需要接线
    

### 第二个阶段： 晶体管计算机

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714385203321/df4813a9-6987-482a-8f00-72be902fbd9e.png align="center")

* 集成度相对较高，空间占用相对小
    
* 功耗相对较低，运行速度较快
    
* 操作相对简单，交互更加方便
    

### 第三个阶段： 集成电路计算机

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714385321880/2e65a93d-2600-4c88-96d3-dc07edc59cfe.png align="center")

* 计算机变得更小
    
* 功耗变得更低
    
* 计算速度变得更快
    

### 第四个阶段： 超大规模集成电路计算机

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714385406130/74f6e357-974c-4e6d-aa4c-98099dad40c8.png align="center")

* 一个芯片集成了上百万的晶体管
    
* 速度更快，体积更小，价格更低，更能被大众接受
    
* 用途丰富： 文本处理、表格处理、高交互的游戏与应用
    

### 第五个阶段： 未来计算机

* 生物计算机
    
* 量子计算机
    

## 微型计算机的发展历史

### 单核CPU

* 1971： 500KHz频率的微型计算机（字长8位）
    
* 1973： 高于 1MHz频率的微型计算机（字长8位）
    
* 1978： 500MNHz 频率的微信计算机（字长16位）
    
* 1985： 高于 1GHz 频率的微型计算机（字长32位）
    
* 2000： 高于 2GHz 频率的微型计算机（字长32位）
    

### 多核 CPU

* 2005： Intel 奔腾系列双核 CPU、AMD速龙系列
    
* 2006： Intel 酷睿四核 CPU
    
* Intel 酷睿系列十六核CPU
    
* Intel 至强系列五十六核CPU
    

# 计算机的分类

## 超级计算机

* 功能最强、运算速度最快、存储容量最大的计算机
    
* 用于国家高科技领域和顶尖技术研究
    
* 标记他们运算速度的单位是 TFlop/s
    

![世界排名](https://cdn.hashnode.com/res/hashnode/image/upload/v1714385983619/03c64d55-9e6c-494f-9392-7ce3106c21ab.png align="center")

![中国排名](https://cdn.hashnode.com/res/hashnode/image/upload/v1714386004254/0c8451a5-3c1b-4f12-83d7-dcc159e44ab1.png align="center")

## 大型计算机

* 又称大型机、大型主机、主机等
    
* 具有高性能，可处理大量数据和复杂的运算
    
* 在大型机市场领域，IBM 占据着很大的份额
    

### 迷你计算机（服务器）

* 也称小型机，普通服务器
    
* 不需要特殊的空调场所
    
* 具备不错的算力，可以完成较复杂的运算
    

### 工作站

* 高端的通用计算机，提供比个人计算机更强大的性能
    
* 类似于普通台式电脑，体积较大，但性能强劲
    

### 微型计算机

* 又称个人计算机时普通的一类计算机
    

# 计算机的体系与结构

## 冯诺依曼体系

将程序指令和数据一起存贮的计算机设计概念结构

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714386569674/add89e45-f9a4-4716-8549-72073d10b3a4.png align="center")

* 能够吧需要的程序和数据送至计算机中
    
* 能够长期记忆程序、数据、中间结果以及最终运算的结果的能力
    
* 能够具备算数、逻辑运算和数据传输等数据加工处理的能力
    
* 能够按照要求将处理结果输出给用户
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714386736309/689ef9ad-bde6-42f8-935b-3e60779a3f56.png align="center")

冯诺依曼瓶颈： CPU和存储速率之间的问题无法调和

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714386803479/649579f8-bf9e-4fa0-87ce-193923179a83.png align="center")

## 现代计算机的结构

* 现代计算机在冯诺依曼体积结构的基础上进行修改
    
* 解决CPU与存储设备之间的性能差异问题
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714386929348/8425f0b9-391a-49f8-a488-795e2aec7e66.png align="center")
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714386960927/fcb90eef-71dd-4dbc-b6d1-e0a6c03dc2ad.png align="center")
    

# 计算机的层次与编程语言

## 程序翻译与程序解释

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714387082562/05b3f425-40c9-4588-9c86-40c87c64ff0a.png align="center")

### 程序翻译

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714387109590/f002409e-3676-46f4-a606-6042993e633d.png align="center")

### 程序解释

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714387137766/9d97a68d-578e-4725-9176-1a0ac81572d6.png align="center")

* 计算机执行的指令都是L0
    
* 翻译过程生成新的L0程序，解释过程不生成L0程序
    
* 解释过程由L0编写的解释器去解释L1程序
    

**程序翻译**

* C/C++
    
* Object-C
    
* Golang
    

**程序解释**

* Python
    
* php
    
* javascript
    

**翻译+解析**

* Java
    
* C#
    

## 计算机的层次和编程语言

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714387465694/904bc9b1-8d27-4959-865a-65ebe8ca6788.png align="center")

### 硬件逻辑层

* 门、触发器等逻辑电路组成
    
* 数据电子工程的领域
    

### 微程序机器层

* 编程语言是微指令集
    
* 微指令所组成的微程序直接交由硬件执行
    

### 传统机器层

* 编程语言是CPU指令集（机器指令）
    
* 编程语言和硬件是直接相关的
    
* 不同架构的CPU使用不同的CPU指令集
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714387634374/1a379340-39fe-4ab8-b691-a4f45decc0c8.png align="center")

### 操作系统层

* 向上提供了建议的操作界面
    
* 乡下对接了指令系统，管理硬件资源
    
* 操作系统层是在软件和硬件之间的适配层
    

### 汇编语言层

* 编程语言是汇编语言
    
* 汇编语言可以翻译成科直接执行的机器语言
    
* 完成翻译的过程的程序就是汇编器
    

### 高级语言层

* 编程语言为广大程序员所接受的高级语言
    
* 高级语言的类别非常多，有几百种
    
* 常见的高级语言有：Python，Java，C/C++，Golang等
    

### 应用层

* 满足计算机针对某种用途而专门设计
    

# 计算机的速度单位

## 容量单位

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714387938972/79be29bd-ee90-467c-8803-7765432d6123.png align="center")

* 在物理层面，高低电平记录信息
    
* 理论上只认识0/1两种状态
    
* 0/1能够表示的内容太少了，需要更大的容量表示方法
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714388042944/deccc0f7-6750-4185-a853-4d2bea254e88.png align="center")

## 速度单位

### 网络速度

1. 为什么电信的100M宽带，测试峰值速度只有12M每秒？
    
    网络常用单位是 Mbps， 100M/s = 100Mbps = 100Mbit/s， 100Mbit/s = (100/8)MB/s = 12.5MB/s
    

### CPU速度

* CPU 的速度一般体现为CPU的时钟频率
    
* CPU的时钟频率的单位一般是赫兹（Hz）
    
* 主流CPU的时钟频率都在2GHz以上
    

# 计算机的字符与编码集

## 字符编码集的历史

### ASCII 码

* 使用7个bits就可以完全表示ASCII码
    
* 包含95个可打印字符
    
* 33个不可打印字符（包括控制字符）
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714388552414/02d6ff8a-3558-4d03-9b53-01e029c49547.png align="center")

### Extended ASCII 码

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714388600775/be85d031-3775-47b9-bb98-5b79b93ccb60.png align="center")

* 常见的数学运算符
    
* 带音标的欧洲字符
    
* 其他常用、表格符等
    

### 字符编码集的国际化

* 欧洲、中亚、东亚、拉丁美洲国家的语言多样性
    
* 语言体系不一样，不以有限字符组合的语言
    
* 中国、韩国、日本等的语言最为复杂
    

## 中文编码集

### **GB2312**

* 《信息交换用汉字编码字符集——基本集》
    
* 一共收录了7445个字符
    
* 包裹了6763个汉字和682个其他符号
    

### GBK

* 《汉字内码扩展规范》
    
* 向下兼容了GB2312，向上支持国际ISO标准
    
* 收录了21003个汉字，支持全部的中日韩汉字
    

### 中文编码集

* Unicode： 统一码、万国码、单一码
    
* Unicode定义了世界通用的符号集，UTF-\*实现了编码
    
* UTF-8以字节为单位对Unicode进行编码
    

# 练习题与答案详解

[习题](https://static.ziying.site/upload/(2.1)--2-9%20%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BB%84%E6%88%90%E5%8E%9F%E7%90%86%E6%A6%82%E8%BF%B0%E7%AF%87%E4%B8%93%E9%A1%B9%E7%BB%83%E4%B9%A0%E9%A2%98%2017%20%E9%81%93.pdf)

[答案详解](https://static.ziying.site/upload/(2.2)--2-10%20%E4%B8%93%E9%A1%B9%E7%BB%83%E4%B9%A0%E9%A2%98%E7%AD%94%E6%A1%88%E6%8F%AD%E6%99%93%E4%B8%8E%E8%A7%A3%E6%9E%90.pdf)

# 计算机组成与人工智能

* 人工智能的发展依赖于算力的发展
    
* 交叉学科： 自然科学、社会科学、技术科学
    
* 安全问题、伦理问题
    

## 图灵测试

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714390016668/ed2efbd5-3643-48af-9431-d7016c0e122b.png align="center")

## 专家系统

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714390064770/dbd93107-f2b5-4757-a6f0-656565375623.png align="center")

## 神经网络

* 图像识别
    
* 推荐系统
    
* 机器人
    
* 自然语言处理
    
* 时序序列预测
    
* 游戏AI
    

## 通用人工智能

* 人工智能研究的终极目标
    
* 弱人工只能处理特定的问题
    
* 通用人工智能是具备与人类同等智慧或超越人类的人工智能