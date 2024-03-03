---
title: "流媒体简介——m3u8"
datePublished: Sun Mar 03 2024 16:23:26 GMT+0000 (Coordinated Universal Time)
cuid: cltbq1m1x000409kz6vulexbv
slug: m3u8
tags: 6keg6akr5lil6l29

---

### **什么是流媒体**

> **流媒体**（英语：**Streaming media**）是指将一连串的[多媒体](https://zh.wikipedia.org/wiki/%E5%A4%9A%E5%AA%92%E9%AB%94)数据压缩后，经过[互联网](https://zh.wikipedia.org/wiki/%E7%B6%B2%E9%9A%9B%E7%B6%B2%E8%B7%AF)分段发送数据，在互联网上即时传输影音以供观赏的一种技术与过程，此技术使得数据[数据包](https://zh.wikipedia.org/wiki/%E5%B0%81%E5%8C%85)得以像流水一样发送，如果不使用此技术，就必须在使用前[下载](https://zh.wikipedia.org/wiki/%E4%B8%8B%E8%BD%BD)整个媒体文件。

### **视频文件格式**

视频文件格式被称为**容器格式**

编码格式则为容器中视频流的压缩编码格式

### **编码格式**

没有编码的数字视频数据量很大储存困难、传输困难

国际上制定视频编码技术的组织有两家：国际电联（ITU-T）、国际标准化组织（ISO）

国际电联：H261、H262、H263+

国际标准化组织：MPEG1、MEPG2、MEPG4

H264 是两个组织联合组件的联合视频组。

### **流媒体**

3 中主流的流媒体协议：HTTP、RTSP、RTMP

HLS（HTTP Live Streaming）是苹果公司提出的基于 HTTP 的流媒体传输协议，在开始会话时客户端会下载一个包含元数据的 extended M3U（m3u8）playlist，用于寻找可用的流媒体

HLS 协议规定：视频封装格式为 ts、视频编码格式是 H264

### **代码仓库**

100 行代码搞定 HTL 下载：[github 地址](https://github.com/caorushizi/mediago)