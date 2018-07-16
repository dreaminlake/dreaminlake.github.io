---
layout: page
permalink: /about.html
title: 关于
tags: [关于, 博客, 梦里依稀的小湖, blog]
---

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" height="52" style="width:280px;margin:0;" src="https://music.163.com/outchain/player?type=2&id=27571001&auto=0&height=32"></iframe>

* 博客网址：[https://dreaminlake.com](https://dreaminlake.com)
* Atom 订阅：[https://dreaminlake.com/atom.xml](/atom.xml)

分享技术、记录点滴，这是 花生米 的个人博客。

请使用 Mozilla Firefox、Google Chrome 等现代浏览器浏览本博客。

本博采用 Jekyll[[1]][1] 搭建，Markdown[[2]][2] 写作，托管于京东云，七牛云存储[[3]][3]和GitHub[[4]][4]。 

自 2008 年 12 月 30 日起，本站已运行 <script>document.write(Math.floor((Date.now() / 1000 - {{ "2008-12-30" | date: "%s" }}) / (60 * 60 * 24)));</script> 天，截至 {{ site.time | date: "%Y 年 %m 月 %d 日" }}，写了博文 {{ site.posts.size }} 篇，{% assign count = 0 %}{% for post in site.posts %}{% assign single_count = post.content | strip_html | strip_newlines | remove: ' ' | size %}{% assign count = count | plus: single_count %}{% endfor %}{% if count > 10000 %}{{ count | divided_by: 10000 }} 万 {{ count | modulo: 10000 }}{% else %}{{ count }}{% endif %} 字。

即日起，本博客的原创内容，均采用知识共享组织（Creative Commons）的“署名-非商业性使用 3.0 中国大陆”（CC BY-NC 3.0 CN[[5]][5]）许可。

## 博主

地球人，拖延症、轻微强迫症患者，喜欢拍照、喜欢骑行、喜欢折腾。

* Email: andrew.l.jing(at)gmail.com

## 博客进程

* 2008-12-30 接触互联网
* 2014-12-25 博客建立，网址 dreaminlake.com，名字为“梦里依稀的小湖”
* 2017-09-01 博客转到 Jekyll 平台，托管于 GitHub
* 2017-09-01 国内解析到阿里云虚拟主机，解析到七牛云存储
* 2018-07-15 国内解析到京东云

## 参考资料

[1]: https://jekyllrb.com/ "Jekyll"
[2]: https://daringfireball.net/projects/markdown/ "Markdown"
[3]: https://portal.qiniu.com/signup?code=3l877e5rpn5ua "七牛云存储"
[4]: https://github.com/ "GitHub"
[5]: https://creativecommons.org/licenses/by-nc/3.0/cn/ "署名-非商业性使用 3.0 中国大陆"
