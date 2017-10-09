---
layout: post
title: Hexo中嵌入HTML5视频
date: 2016-06-20 18:28:26+0800
thumb: IMG_PATH/avatar.jpg
tags: [Hexo, HTML5, 视频, video]
category: tech
---
这里表扬哈腾讯，国内几家视频网站，就鹅厂的可以自动切换Flash和html5视频，不装flash插件，也能愉快的追剧啦！HTML5正在逐渐的挤占Flash市场，Google已经宣称放弃Flash，转向HTML5，它家吸金产品Adwords，从2016年6月30日起，将不能再上传采用Flash制作的展示广告，自2017年1月起，AdWords将停止投放采用Flash格式的展示广告。网页开发者转向HTML5,Adobe也发布公告称，将鼓励内容创作者采用新的网络标准，例如HTML5，而不是Flash。
Hexo博客中可以插入腾讯优酷等网站的视频，倒是可以直接引用网站的代码，但是不管是用embed还是iframe，都采用的flash播放，就引出了资源占有率高、风扇声阵阵、长时间后发热、不可避免的广告、移动端的不兼容。

        <video width="100%"  src="视频地址" controls loop>Your browser does not support the <code>video</code> element.</video>

当换成上面的代码进行HTML5视频嵌入后，广告没了、风扇不响了、资源占有率低了、貌似也不怎么发热了、手机上也能观看了，是不是很开薪啊。
 
          HTML5<video>标签：
          width，视频播放器宽度属性，这里用100％表示自适应
          controls，显示控件属性，比如播放按钮、进度条、全屏等
          loop，循环属性，当媒介文件完成播放后再次开始播放
          src，要播放的视频的url
          autoplay，自动播放属性，视频就绪后马上播放，慎用
          height，视频播放器高度属性
          muted，音频静音属性，视频的音频输出被静音