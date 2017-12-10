---
title: sublime_install
date: 2017-12-10 20:43:40
tags: -sublime
---
只是装个sublime-text，简直要了亲命了！
![](/images/juewang.jpg)

## 起因 ##
之前因为ros的缘故，装的是kubuntu 14.04，但是UI丑到无法忍受啊。想要安装个teamviewer结果依赖项还不给更新到更新的版本。一怒之下，安装了kubuntu 16.04.

新的系统当然要用新的文本编辑器咯。
![](/images/dese.jpeg)

结果呢，不管是采用官方网站给出的步骤还是采用第三方ppa安装方法，就是无法安装成功。官方步骤直接卡在gpg key阶段，ppa则是死活下载不下来……
![](/images/xianzhuo.jpg)

没有好梯子啊。蓝灯不亮啊！（还TMD改firefox的proxy选项,差点让我又重装一遍系统）

## 波折 ##
后来尝试了用deb安装了个3083。结果安装package control又有问题……
![](/images/juewang.jpg)

没办法，只好用最后一个办法了，使用tarball安装。就是下载压缩包，解压，然后自己擦屁股。
![](/images/jianqiang.jpg)

## 言归正传 ##
好，不用apt，不用deb，来一步步安装sublime-text-3143

### 下载tarball ###
去sublime-text的[官网](https://www.sublimetext.com/3)下载
![](/images/snip/sublime.png)

解压缩
```shell
tar -xvf your-sublime-tar-file
```


### 移动文件 ###
将解压缩后的文件夹移动到``\opt``文件夹下
```shell
sudo mv sublime_text_3 \opt
```
>/opt 
这里主要存放一些可选的程序。如你想尝试最新的firefox测试版吗？那就装到/opt目录下吧，这样，当你尝试完，想删掉firefox的时候，你就 可以直接删除它，而不影响系统其他任何设置。安装到/opt目录下的程序，它所有的数据、库文件等等都是放在同个目录下面。

### 为sublime-text创建bash命令 ###
其实就是把sublime-text的运行脚本复制到``/usr/bin``文件夹下，不过我们可以用symbolic link来避免重复的文件占用
```shell
sudo ln -s /opt/sublime_text_3/sublime_text /usr/bin/sublime
```

如此这般，你就可以在shell中通过输入``sublime``来启动sublime-text了。

当然，如果你觉得sublime有点长，可以在``~/.bashrc``文件的最后加上
```shell
alias subl=sublime
```

### 让sublime可以在启动器中打开  ###
其实就是创建快捷方式啦。如果不够lucky的话，你可能需要自己写一个``.desktop``文件。但是，在解压缩的文件中已经有啦。(●ˇ∀ˇ●)，所以我们要做的就是把这个文件拷贝到``/usr/share/applications/``文件夹下
```shell
sudo cp /opt/sublime_text_3/sublime.desktop /usr/share/applications
```

别急，还有个坑！

用新安装的sublime-text看看，这个desktop文件的``Exec``对不对。不对的话启动器可是会报错的哦！ԅ(¯﹃¯ԅ)

至此，sublime-text安装完成！
![](/images/bingo.jpg)

## 写在后面 ##
之后当然是安装各种插件啦！
1. package control
2. anaconda
3. sublimerepl
4. markdownediting
5. omnimarkuppreviewer
