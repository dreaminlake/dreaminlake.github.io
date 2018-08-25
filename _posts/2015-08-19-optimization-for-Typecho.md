---
title: Typecho个性化优化常用解决方法
tags: [typecho]
date: 2015-08-19 22:01:00+0800
layout: post
thumb: IMG_PATH/avatar.jpg
category: tech
---

一.Gravatar头像图片显示问题

第一种方法还是用Gravatar头像，需要修改typecho文件，程序升级后需要重复修改，即在var/Typecho/Common.php的第939行将www.gravatar.com中的www.去掉！=>现在我也是用的该方法，借鉴于[不带诗情画意]

第二种方法是使用本地头像，即使用头像缓存插件，请找度娘......

第三种方法是使用第三方评论插件，目前使用较多的还是多说和畅言，前者用户体验还可以,但是要注意以后那一天想找回评论信息的问题，和多说服务器宕机不稳定的情况；后者基于搜狐提供的，界面一般，但服务器是比较稳定的。

![typecho优化](https://ww2.sinaimg.cn/mw600/005PvELHgw1f4dhxw56vej30dy07fmy0.jpg)

二.返回网页顶部代码

在footer.php页面增加如下代码（可直接参考我的JS代码，注意将其中的图片定义为你自己喜欢的）：
  
<!-- Start of Go-Top Code -->
<script type="text/javascript" src="https://qiniu.dreaminlake.com/jquery-1.11.1.min.js"></script>
<script type="text/javascript" src="https://qiniu.dreaminlake.com/go-top.js"></script>
<!-- End of Go-Top Code -->
  

三.UEditor for Typecho插件安装

百度官方推荐的UEditor for Typecho第三方插件，支持Typecho 1.0/0.9/0.8。

1、下载和安装

注：Typecho 1.0/0.9用户请在[控制台/个人设置]中关闭Markdown解析再启用插件！

1）百度搜索百度编辑器，官方直接下载zip压缩包。

2）解压后，将 UEditor 文件夹放入 /typecho/usr/plugins/ 下，然后到Typecho后台启用插件即可。

2、修改主题文件

为了在页面展示中显示语法高亮，还需要修改一下主题文件，在 footer.php 中加入如下代码：
  
<!--加入高亮的js和css文件，如果你的编辑器和展示也是一个页面那么高亮的js可以不加载-->
<script type="text/javascript" src="<?php $this->options->siteUrl(); ?>usr/plugins/UEditor/ueditor/third-party/SyntaxHighlighter/shCore.js"></script>

<link rel="stylesheet" type="text/css" href="<?php $this->options->siteUrl(); ?>usr/plugins/UEditor/ueditor/third-party/SyntaxHighlighter/shCoreDefault.css"/>

<script type="text/javascript">
     //为了在编辑器之外能展示高亮代码
      SyntaxHighlighter.highlight();
   // UE.getEditor('myEditor');
</script>
  

3、SyntaxHighlighter语法有错行的现象，代码过长还会超出展示区域，就需要修改UEditor插件下third-party\SyntaxHighlighter\shCoreDefault.css样式文件：

1）.syntaxhighlighter td.code .line修改成：
  
.syntaxhighlighter td.code .line {
    padding: 0 1em !important;
    white-space: nowrap;
}
  
2）.syntaxhighlighter a,.syntaxhighlighter div,.syntaxhighlighter code,.syntaxhighlighter,.syntaxhighlighter td,.syntaxhighlighter tr,.syntaxhighlighter tbody,.syntaxhighlighter thead,.syntaxhighlighter caption,.syntaxhighlighter textarea
  
.syntaxhighlighter a,.syntaxhighlighter div,.syntaxhighlighter code,.syntaxhighlighter,.syntaxhighlighter td,.syntaxhighlighter tr,.syntaxhighlighter tbody,.syntaxhighlighter thead,.syntaxhighlighter caption,.syntaxhighlighter textarea{
    overflow: visible !important;
}
  
把overflow:&nbsp;visible&nbsp;!important;样式去掉

3）.syntaxhighlighter td.code .container修改成：
  
.syntaxhighlighter td.code .container{
    width: 632px;
    word-wrap: break-word;
    overflow-x: auto;
    position:relative!important
}
  
其中，width的值请根据页面进行调整

OK，这样子，PC和移动端打开，都不会出现由于代码过长超出展示区域的现象了。
