title: mac批量重命名之MPlayerX顺序播放解决方案
tags: []
date: 2015-08-13 17:20:49
---

这段日子以一个脱离程序员生活的角色存在着.告别了快节奏,嘈杂的工作环境和思绪混乱的个人状态,心情也平复了不少.算是培养点高雅的兴趣吧,其实就是让手不闲下来,让闲暇的时光稍有意义. 抄起哥们的吉他练了起来. 跟着大伟的教程学习发现吉他学习也不是那么遥不可及.其实兴趣确实是最好的老湿,互联网让学习变得不在那么依赖课堂的教学和空间的限制. 又扯远了….

其实本文主要是想交待和记录,在用Mac下的MplayerX观看 大伟吉他系列教程 时遇到MPlayerX不支持播放列表(playlist)的问题,但是MPlayerX默认支持同目录下顺序文件名播放的功能,通过修改文件名来实现系列教程的顺序播放.

<!-- more -->

## 问题

Mac下的批量修改文件名其实有很多方法…

比如 纯手工模式 如果这你也能接受的话, Orz 我只能这样了

通过automator添加一个批量操作.具体的操作细节不再赘述.在这里不能满足我的要求.因为我的文件名规则中需要设计到一些_正则替换_(关于什么是`正则替换`请自行google)

最后还是不得不回到程序员的固有思维,用终端shell命令来实现.

### MAC OS NTFS 读写问题

坑爹的事发生了.我的视频文件全部存放在移动硬盘(128G的Pro伤不起的说),而移动硬盘的分区格式采用NTFS,这在Mac下默认只支持读不支持写的.Orz,再次泪奔…

好吧,已经开始了,就不能让那钻牛角尖的劲停下来.最终找到了Mac下对NTFS格式U盘/移动硬盘读写的方案,安装Paragon NTFS for Mac OS X,官方下载链接[NTFS for Mac® OS X 11 中文版

][1](http://www.paragon-software.com/cn/home/ntfs-mac/),希望能支持正版.对于伤不起的用户,这里低调的发个链接好了[要番羽土啬](http://docs.google.com/file/d/0B6JwEJUWTkcrMlVtTHlJYmpsZms/edit?pli=1).(对于不知到怎么番羽土啬的就不要问我了,自行想办法吧)

好了,通过上面的工具,移动硬盘读写的问题解决了.

## RENAME 批量改名

### 安装 rename

接下来就是批量改名了.虽然通过find,sed可以轻松解决,但是通过知乎上不少知友给出的解决方案,个人认为Mac上rename绝对是个不可多得的好工具.Mac上使用rename,需要

    brew install rename

### 去末尾数字

然后我的视频文件名格式为:![QQ20140902-1@2x.png](http://zozorz-typechoupload.stor.sinaapp.com/1992525744.png)

首先,将末尾的’-数字’去掉

    rename 's/(第[0-9]+课)(-[0-9]+).wmv/$1.wmv/' *.wmv

稍微讲解下上面的命令意思:

`s/..../../` 为rename命令的正则替换格式,其中第一个’/ /‘之间的为正则表达式,第二个’/ /‘之间的为要替换的内容.

`[0-9]`表示 0到9的任何数字, `+` 表示前面的数字可以组合出现至少一个,比如1,01,09,900都可以,`()`之间的内容又可以看做一个子表达式.使用`()`的目的是为了后面的替换是可以直接拿到前面匹配出的内容. 比如通过运行上面的命令, 将 ‘第10课-10.wmv’ 替换成 ‘第10课.wmv’.其中第二个’/ /‘中的$1就表示第一个’/ /‘中匹配出的’第10课’.

### 数字位数统一

通过上面的操作去掉了不需要的’-数字’部分,要使得MplayerX正确读取顺序,需要注意’需要将 ‘第1课’ 改为’第01课’(这个跟MplayerX的默认排序规则有关).同理,用rename也很简单可以实现:

    rename 's/第([1-9])课.wmv/第0$1课.wmv/' *.wmv

Ok,通过上面的操作,再次回到视频目标目录,通过MPlayerX打开其中一个视频,然后点击播放下一个,顺利按照我们预期的顺序开始播放.Well done!