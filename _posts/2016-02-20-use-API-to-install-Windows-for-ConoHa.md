---
title: ConoHa利用API安装Windows
tags: [ConoHa,Windows,API,VPS]
date: 2016-02-20 11:48:00+0800
layout: post
thumb: IMG_PATH/avatar.jpg
category: tech
---

本文尝试在Conoha东京机房，利用API来安装Windows2003，需要用于安装Windows2003的VPS、Xshell等工具（主要是连接上你的VPS并进行命令输入，或者其它VPS）、windows2003的镜像地址。
1. 找到你的账户的API信息，默认是没有添加API账户的，需要我们自己先添加新的API账户。
2. 保证要安装的windows2003的VPS处于关机状态，通过Xshell等工具或者其它VPS，执行以下命令，获取会话的X-Auth-Token，便于上传、挂载iso：

curl -i -X POST \
-H "Accept: application/json" \
-d '{
"auth": {
	"passwordCredentials": {
	"username": "API用户用户名",
	"password": "API用户密码"
    },
"tenantId": "店铺ID"
}
}' \
https://identity.tyo1.conoha.io/v2.0/tokens

3. 通过2中返回的id后的"id":"=>X-Auth-Token，上传iso，执行以下命令：

curl -i -X POST \
-H 'Content-Type: application/json' \
-H "Accept: application/json" \
-H "X-Auth-Token: X-Auth-Token信息" \
-d '{
	"iso-image": {
	"url": "windows2003地址"
    }
}' \
https://compute.tyo1.conoha.io/v2/店铺ID/iso-images

4. 查看3中上传的iso信息，可重复执行此步骤，以确保iso上传成功,并获取iso的路径：

curl -i -X GET \
-H 'Content-Type: application/json' \
-H "Accept: application/json" \
-H "X-Auth-Token: X-Auth-Token信息" \
https://compute.tyo1.conoha.io/v2/店铺ID/iso-images

5. 通过4中获得的"/mnt/isos/repos/tenant_iso_data/店铺ID/win03_x64.iso"，挂载iso，执行以下命令：

curl -i -X POST \
-H "Accept: application/json" \
-H "X-Auth-Token: X-Auth-Token信息" \
-d '{"mountImage": "/mnt/isos/repos/tenant_iso_data/店铺ID/win03_x64.iso"}' \
https://compute.tyo1.conoha.io/v2/店铺ID/servers/UUID信息/action

6. 等待5挂载后，通过以下命令查看已经挂载的iso：

curl -i -X GET \
-H "Accept: application/json" \
-H "X-Auth-Token: X-Auth-Token信息" \
https://compute.tyo1.conoha.io/v2/店铺ID/servers/UUID信息

7. ConoHa账户后台，VPS开机，VNC链接安装Windows2003，就大功告成了
![大功告成](https://ww2.sinaimg.cn/mw600/005PvELHgw1f4dh9yfy58j30i20h3ju3.jpg)
