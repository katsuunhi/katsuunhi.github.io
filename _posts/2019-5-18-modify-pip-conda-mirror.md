---
layout:     post
author:     "Katsu"
date:       2019-05-18 08:46:00
title:      windows修改pip和conda镜像源
---

>在使用pip安装一些python模块的时候，最让人头疼的就是网速，一个10K/s的网速真的是气死个人。为了方便使用，我们可以通过以下办法修改pip安装的镜像源，将原始的国外镜像源改成国内的镜像，话不多说，铁汁们，相位猛冲。

<br>
### 1. windows下修改pip镜像源步骤

    (1):在windows文件管理器中,输入 %APPDATA%，进入文件夹"C:\Users\Administrator\AppData\Roaming"

    (2):会定位到一个新的目录下，在该目录下新建pip文件夹，然后到pip文件夹里面去新建个pip.ini文件

    (3):在新建的pip.ini文件中输入以下内容

```
[global]
timeout = 6000
index-url = https://pypi.tuna.tsinghua.edu.cn/simple 
trusted-host = pypi.tuna.tsinghua.edu.cn
```

>比较常用的国内pypi镜像源有清华和豆瓣，教育网当然还是用清华，速度10M/s，直接起飞
>>豆瓣：http://pypi.douban.com/simple/ <br>
>>清华：https://pypi.tuna.tsinghua.edu.cn/simple 

<br><br>
### 2. conda镜像源修改
>目前清华的镜像源已经不能用了，中科大的镜像源貌似还可以用

```
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
```

>修改好了之后会在用户目录下生成一个.condarc文件，里面是配置信息，可以直接在里面添加或者删除链接

<br>
##### 改回原镜像源

```
conda config --remove-key channels
```