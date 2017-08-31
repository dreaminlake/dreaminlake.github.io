---
title: centos下用curl监控网站运行状态
tags: [centos,监控]
date: 2014-12-02 21:28:00+0800
layout: post
thumb: IMG_PATH/avatar.jpg
category: tech
---

在centos环境，使用curl抓取网站页面，编写shell脚本，crontab添加计划任务，最终达到监控网站的运行状态。

root用户先创建监控目录：
  
mkdir /root/monitor
  

建立监控shell脚本：
  
touch /root/monitor/monitor.sh
  

用vi编辑monitor.sh ：
  
#!/bin/bash
#purpose:monitor webserver status code
#how to:run the script every 1 minutes with crontab
log_path="/root/monitor/atge.log"
error_log_path="/root/monitor/atge_error.log"
URL="http://dreaminlake.com/"
HTTP_CODE=`curl -o /dev/null -s -w "%{http_code}" "${URL}"`

echo "`date '+%Y-%m-%d %H:%M:%S'` visit code = $HTTP_CODE">>$log_path
if [ $HTTP_CODE != 200 ];then

echo "`date '+%Y-%m-%d %H:%M:%S'` visit error !!! code = $HTTP_CODE">>$error_log_path
fi
exit 0
  

添加执行权限：
  
chmod 777 /root/monitor/monitor.sh
  

添加计划任务：
  
crontab -e
*/1 * * * * /root/monitor/monitor.sh
  

  好了，这样子每分钟curl就抓取dreaminlake.com页面一次

  返回正常访问值200就记录到 /root/monitor/atge.log 里

  不能正常访问非200时就记录在 /root/monitor/atge_error.log 里

  当然，大家可以根据自己的需求进行扩展
