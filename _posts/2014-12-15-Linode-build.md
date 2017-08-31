---
title: Linode的配置和部署
tags: [Linode,配置]
date: 2014-12-15 12:04:00+0800
layout: post
thumb: IMG_PATH/avatar.jpg
category: life
---

Linode VPS 控制后台可以让我们方便快捷的创建一个新的磁盘和安装全新的Linux操作系统，让我们来看看具体的操作步骤：

1.登陆Linode 控制后台. =&gt; [https://manager.linode.com/](https://manager.linode.com/)  =&gt; 注意这里的Username 和 Password是您拍下宝贝时所附的账户和密码信息.

2.点击控制面板下的 Linodes ，列出所有的VPS.

3.选择一个Linode VPS，进入Dashboard.

4.点击 Deploy a Linux Distribution.

5.在 Distribution下拉列表中选择您要安装的Linux发行版本，也可以选择使用 StackScripts，通过脚本直接安装操作系统及必要的软件，并配置系统.

6.在Deployment Disk Size中填写磁盘大小，必须小于Linode剩余的待分配空间.

7.Swap Disk 菜单一般使用默认选项即可，这里建议默认值就好.

8.输入Root密码，这里要记住，后面用SSH远程工具登录时必备.

9.再点击 Deploy就完成了系统的创建.

10.最后一步，点击boot，就启动VPS了.