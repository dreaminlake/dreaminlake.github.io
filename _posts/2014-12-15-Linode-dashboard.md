---
title: Linode控制台介绍
tags: [Linode,控制台]
date: 2014-12-15 22:07:00+0800
layout: post
thumb: IMG_PATH/avatar.jpg
category: life
---

本文介绍哈由Linode自己独立开发与维护的Linode VPS的控制面板，方面大家管理自己的VPS，先上图给大家过过眼~o~
Dashboard部分介绍

这部分是VPS项目配置，点击图中的 My Centos 7 Profile，就可以进入配置这台VPS的一些内核等信息

Edit | Remove 对应 编辑|删除配置, Reboot 对应 重启VPS系统, Rebuild | Deploy a Linux Distribution | Create a new Configuration Profile 分别对应 重建 | 部署Linux发行版本 | 创建一个新的配置&nbsp;

Rebuild（重建系统），是将该VPS全部重新部署，之前的系统等都会清理；这里可以选择系统、设置系统盘占用大小、swap大小、以及root密码&nbsp;
Distribution（选择系统）, Deployment Disk Size（设置系统盘大小）, Swap Disk（Swap大小）, Root Password（Root密码）&nbsp;
Deploy a Linux Distribution（部署Linux发行版本），需要VPS有空闲的硬盘大小，才可以创建，类似一台主机安装多个系统，通过引导正常的系统，来修复损坏的系统等&nbsp;
Distribution（选择系统）, Deployment Disk Size（设置系统盘大小）, Swap Disk（Swap大小）, Root Password（Root密码） 填写好后就可以创建一个新的系统&nbsp;
Create a new Configuration Profile （创建一个新的配置） 例如有多个分区、系统，来设置主机启动时，需要加载哪些分区信息，或者启动参数等，此功能需要和Deploy a Linux Distribution配合使用&nbsp;
Label（名称）, Notes（描述）, Kernel（linux内核版本）, Run Level（运行级别）, Memory Limit（内存限制大小）, Block Device Assignment 可以设置磁盘对应的硬盘信息, root device 设置启动的磁盘信息&nbsp;
此处，特别提示：只重新安装系统盘（更换系统），删除磁盘，使用Deploy a Linux Distribution，来安装系统，先停止主机，将安装系统的硬盘删除，在使用Deploy a Linux Distribution功能来创建系统，在选择新创建的系统配置，点击boot来启动主机&nbsp;
>

Disk Images（磁盘映像）介绍&nbsp;
Edit是编辑磁盘, Remove是删除磁盘，创建磁盘, Type是设置硬盘格式，创建磁盘, Size是设置创建磁盘的大小

Host Job Queue（历史记录）介绍&nbsp;
Graphs（资源监控）介绍&nbsp;
Dashboard 侧边栏介绍&nbsp;
Server Status是VPS的状态

显示Powered Off，说明这台VPS是停止状态，显示Running，说明VPS在运行中, Shut down就是关机，x day uptime，就是已经运行了x天&nbsp;
Network是VPS的网络流量使用信息&nbsp;
Transfer/mo 2000 GB #这个是每月的流量限额，2000GB, &nbsp;Incoming 91.4MB #进入的流量91.4MB , &nbsp;Outgoing: 394MB #输出的流量394MB, Total: 486MB #总的流量统计是486MB&nbsp;
Storage是VPS的磁盘使用信息&nbsp;
Total: 24576 MB #总共硬盘大小, Used: 24576 MB #已经使用大小, Free: 0 MB #空闲大小&nbsp;
Backups是备份信息&nbsp;
显示No-Enabled，指这台VPS的备份功能是没有开启的&nbsp;
Host是VPS所在的机房信息&nbsp;
dollas767 idle, online Load
![](https://ww2.sinaimg.cn/mw600/005PvELHgw1f4digekpmoj30ic0ic0x7.jpg)
