---
layout: post
title: Debian8 科学上网
date: 2016-06-18 20:03:11+0800
thumb: IMG_PATH/avatar.jpg
tags: [debian,科学上网,ss,pptp]
category: tech
---
测试环境：debian-8.0-x86_64-minimal

使用root登录，确保VPS服务器支持TUN/TAP及PPP后，执行以下步骤，

1. pptpd安装
  
        apt-get install pptpd -y
  

2. 内网私有IP指定
  
        vi /etc/pptpd.conf
  
vi命令后，直接在文件末尾添加下面两行文字，localip是VPS的私有地址，remoteip是分配给VPN客户端的，
  
        localip 10.0.0.1
        remoteip 10.0.0.100-200
  
按ESC键后，输入:wq退出并保存vi，后续的都记得要保存文件并退出编辑器。

3. DNS服务器设定
  
        vi /etc/ppp/pptpd-options
  
输入/ms-dns，查找ms-dns的两行文字，去掉前面的#符号，修改或者直接在后面加以下内容，
  
        ms-dns 8.8.8.8
        ms-dns 8.8.4.4
  
8.8.8.8和8.8.4.4是Google的公共DNS服务器。

4. VPN用户账号和密码设定
  
        vi /etc/ppp/chap-secrets
  
格式如下:
用户名 <tab> * <tab> 密码 <tab> *
注意此处用tab键将用户名、密码及*分开。

5. MTU设置
  
        vi /etc/ppp/ip-up
  
在文件的末尾添加，
  
        ifconfig $1 mtu 1400
  
6. iptables设置，PPTP协议同防火墙，直接执行下面的命令，
  
        iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
        iptables --table nat --append POSTROUTING --out-interface ppp0 -j MASQUERADE
        iptables -I INPUT -s 10.0.0.0/8 -i ppp0 -j ACCEPT
        iptables --append FORWARD --in-interface eth0 -j ACCEPT
        iptables -t nat -A POSTROUTING -j SNAT --to-source VPS公网地址
  
为了防止VPS关闭、重启或崩溃后，不能用，执行，
  
        vi /etc/rc.local
  
添加下面内容到exit 0的前面，
  
        iptables -t nat -A POSTROUTING -j SNAT --to-source VPS公网地址
  
执行下面命令，写入防火墙设置，
     
        iptables-save > firewall
  
7. 转发启用，用vi编辑sysctl文件，并使net.ipv4.ip_forward=1生效，
  
        vi /etc/sysctl.conf
  
用/net.ipv4.ip_forward=1，找到并去掉前面的#号，输入下面的命令以使更改生效
  
        sysctl -p
  
8. pptpd服务重启，就可以去感受PPTP的科学上网的魅力了哈，
  
        /etc/init.d/pptpd restart
  
