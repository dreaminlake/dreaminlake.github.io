---
title: centos下用sendmail配置简单的邮件服务器
tags: [centos,邮件]
date: 2014-12-03 23:46:00
layout: post
thumb: IMG_PATH/avatar.jpg
category: tech
---

昨天实现了centos下用curl监控网站运行状态，log分为了所有记录和错误记录的文件，就有想当网站不能正常访问时，可以用邮件将错误日志传给网站所有者，再利用手机随时收取邮件掌控网站运行状态。

sendmail邮件系统则很好的扮演了这个角色，但是sendmail默认发出邮件的邮箱源地址，不做修改情况下是形如root@localhost.localhost，这样寄出的邮件基本上都被认定为SPAM（垃圾邮件），所以就需要进行邮件域名配置了。

首先，我们先来安装sendmail服务，CentOS 7 默认是安装了的，如果检测到没有安装sendmail，就只有手动安装了：
  
yum install -y sendmail
yum install -y sendmail-cf
  
接着，我们通过m4来配置sendmail，配置后重启以使配置文件生效：
  
m4 /etc/mail/sendmail.mc > /etc/mail/sendmail.cf
service sendmail restart
  
m4是包在sendmail-cf中的，如果不能识别m4命令，请老老实实的回上一步安装sendmail-cf软件包吧。

然后，为了防止邮件不被认定为SPAM，接下来进行邮件域名配置：

用vi打开local-host-names文件
  
vi /etc/mail/local-host-names
  
按键盘上的i键进行输入，编辑添加域名在其中
  
dreaminlake.com
  
按键盘的ESC键，输入!wq保存local-host-names后强制退出

同样用vi打开submit.cf文件
  
vi /etc/mail/submit.cf
  
找到行 #Dj$w.Foo.COM，修改为
  
Djatge.net
  
同样保存后，配置就结束了，重启sendmail服务以使配置文件生效

再到域名DNS服务商提供的面板去添加下面两条记录

添加域名A记录mail，直接指向邮件服务器的IP地址

添加或是修改域名的MX记录，形如@  MX  dreaminlake.com

使用nslookup检测MX记录是否能正确解析到邮件服务器：
  
#nslookup
set q=mx
dreaminlake.com
  
最后，确保解析生效后，就可以用sendmail来测试发邮件了：

先来测试通过文件内容发送邮件： 首先用touch创建一个mailtest.txt文件：
  
touch mailtest.txt
  
用echo写入内容：
  
echo 'This is test mail'>mailtest.txt
  
发送邮件：
  
mail -s 'Test mail' admin@dreaminlake.com < mailtest.txt
  
好了，可以到邮箱里去收名为‘Test mail’的邮件了

当然，我们还可以使用管道符直接发送邮件内容：
  
echo "This is test mail" | mail -s 'Test mail' admin@dreaminlake.com
  
同样，可以到邮箱里去收名为‘Test mail’的邮件了
