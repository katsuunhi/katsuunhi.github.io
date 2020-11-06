---
layout:     post
title:      "ubuntu2010 使用anaconda安装fastai_v2"
date:       2020-11-6 15:41:00
author:     "Katsu"
---


## fastai_v2的安装教程

>操作系统：ubuntu2010<br>
>nvidia驱动版本：455.28<br>
>cuda版本：11.0.221<br>
>python版本：3.8.3<br>
>anaconda版本：4.9.1<br>
>pytorch版本：1.7.0<br>
>fastai版本：2.1.3
<br>

## 安装过程：
1. 安装ubuntu2010系统<br><br>
2. 安装nvidia driver<br><br>
3. 安装cuda<br><br>
4. 安装anaconda<br><br>
5. 安装fastai<br><br>


### 1. 安装ubuntu2010系统
准备材料：优盘，ubuntu2010镜像文件<br>
镜像文件可以从任意镜像站下载，例如：http://mirrors.ustc.edu.cn/ubuntu-releases/20.10/
<br>

终端中输入
```bash
    usb-creator-gtk
```
制作优盘启动盘（需要格式化）<br>

重启，进入bios修改boot顺序，改为从usb启动，具体方式根据主板型号不同有所区别<br>

按步骤安装系统<br><br>


### 2. 安装nvidia driver
ubuntu2010中的软件和更新-附加驱动中直接安装
<br><br>

### 3. 安装cuda

```bash
    sudo apt update
    sudo apt install nvidia-cuda-toolkit
```
<br><br>

### 4. 安装anaconda
官网：https://www.anaconda.com/products/individual#linux<br>
下好包之后 bash ./包名.sh运行安装程序
<br>
注意可能会默认安装在/root/目录下，权限问题会比较麻烦，建议安装在/home/user-name/anaconda3/<br>

修改权限：<br>
```bash
    sudo chmod 777 -R anaconda3
```
修改conda镜像（清华的镜像不太稳定，建议中科大）<br>

```bash
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/                                            
    conda config --set show_channel_urls yes
```
<br><br>

### 5. 安装fastai
```bash
    conda install -c fastai -c pytorch -c anaconda fastai gh anaconda
```
中间有的包如果太慢，可以手动下载，然后本地安装<br>
比如：
```bash
    conda install --use-local cudatoolkit-11.0.221-h6bb024c_0.tar.bz2 
```
之后终端中输入python
```bash
    ➜  ~ python
    Python 3.8.3 (default, Jul  2 2020, 16:21:59) 
    [GCC 7.3.0] :: Anaconda, Inc. on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import fastai
    >>> fastai.__version__
    '2.1.3'
```

安装成功<br><br>

注意：fastai_v2和v1区别很大，具体参考v2的教程：https://docs.fast.ai/