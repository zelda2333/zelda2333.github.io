---
layout: post
title:  Ubuntu 安装Sublime3
---
### 安装
#### 官网下载
[官网链接：https://www.sublimetext.com/3][1]


解压到 /opt 目录
```
$ cd /opt
$ sudo tar jxvf　/home/zelda/Downloads/sublime_text_3_build_3143_x64.tar.bz2
```
解压后,进入”sublime_text_3”,运行”sublime_text”可执行文件

    $ ./sublime_text

运行成功
![][2]

#### 使用subl运行sublime
写一个名为”subl”的 SHELL 脚本文件, 内容如下:

    #!/bin/sh
    exec /opt/sublime_text_3/sublime_text "$@"


修改权限,并把复制到 /usr/bin 目录下
```
$ chmod a+x subl
$ cp subl /usr/bin/
```
### 中文输入
```
git clone https://github.com/lyfeyaj/sublime-text-imfix.git
cd sublime-text-imfix && ./sublime-imfix
```
然后重启Sublime Text3即可

### 安装Packeage Control
#### 首选方法
在终端输入subl打开sublime text3, 使用快捷键ctrl + `(ESC下面的键),在弹出的控制台中输出以下代码:

    import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
    
  待粘贴python代码的网址是：[https://packagecontrol.io/installation][4]
，根据是sublime text 3或者sublime text 2选择代码进行粘贴。
  但是由于我的电脑无法FQ，因此会提示我网络不可达错误

#### 手动安装

从git下载Package  Control文件到~/.config/sublime-text-3/Packages/

    cd ~/.config/sublime-text-3/Packages/
    git clone https://github.com/wbond/package_control_channel.git
    
1. 点击Preferences > Browse Packages菜单；
2. 进入打开的目录的上层目录，然后再进入Installed Packages目录；
3. 在[https://sublime.wbond.net/Package%20Control.sublime-package][5]下载Package Control.sublime-package，并将该文件复制到Installed Packages目录；
4. 重启Sublime Text。

验证package control安装成功：在菜单栏Preferences --> Package Control调出Package Controller，输入Package Control：Install Package，观察左下角，会提示安装成功。

#### 使用Install Package出现There are no packages available for installation问题

分析原因发现，在利用sublime进行插件下载时，sublime会调用channel_v3.json文件，点击Preferences->Package Setting->Package Control ->Setting Default，可以看到该文件是放置在网络中进行读取的，而由于GFW的原因，导致无法读取该文件

在Preferences->Package Setting->Package Control ->Setting User 中，可以进行用户设置，我们可以将文件下载后，进行本地访问。首先访问[https://packagecontrol.io/channel_v3.json][6] ，将源代码复制后，新建文件为channel_v3.json（也可以从github中获取源文件），然后在Setting User设置中，添加代码，至此，就可以正常使用install package下载插件。
![][3]


参考资料：

[Ubuntu16.04 安装Sublime Text 3 并解决中文输入问题][7]

[Ubuntu中安装Sublime Text 3并安装Package Control][8]

[解决sublime text 3使用Install Package时出现There are no packages available for installation问题][9]

  [1]: https://www.sublimetext.com/3
  [2]: /images/sublime1.png
  [3]: /images/sublime2.png
  [4]: https://packagecontrol.io/installation
  [5]: https://sublime.wbond.net/Package%20Control.sublime-package
  [6]: https://packagecontrol.io/channel_v3.json
  [7]: https://blog.csdn.net/lu_embedded/article/details/79558280
  [8]: https://www.cnblogs.com/bywallance/p/6776943.html 
  [9]: https://www.cnblogs.com/jellify/p/9522477.html




