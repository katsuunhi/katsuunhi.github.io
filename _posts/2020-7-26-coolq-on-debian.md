---
layout:     post
title:      "在debian上安装coolq机器人"
date:       2020-7-26 18:39:00
author:     "Katsu"
---


### 1. 安装docker

使用官方安装脚本自动安装
```bash
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
```
也可以使用国内daocloud一键安装命令：
```bash
curl -sSL https://get.daocloud.io/docker | sh
```

### 2. 创建文件目录
```bash
mkdir /root/coolq-data #可修改
mkdir /home/user
mkdir /home/user/coolq
touch /home/user/.Xauthority
```
### 3. 下载镜像
```bash
docker pull coolq/wine-coolq
```

### 4. 运行镜像
```bash
docker run --name=coolq --restart=always -p 8080:9000 -v /root/coolq-data:/home/user/coolq -e VNC_PASSWD=xxxxxxxx -e COOLQ_ACCOUNT=QQ coolq/wine-coolq
```

>**参数说明**：
>>__coolq__ ：容器名称，可更改，用于启动、停止容器，命令为docker start/stop coolq。创建多个机器人时使用不同容器名与端口即可。
>
>>__--restart=always__ ：官方文档中给的是--rm，--rm的含义是容器停止后删除容器，而--restart=always则表示容器停止后保留并自动运行，这样无论是重启了服务器还是重启docker，都能保证机器人的正常自动运行。
>
>>**12345678**：控制面板[noVNC]的登陆密码。这个可以改，字符不要超过八位，超过貌似不识别。
>
>>**8080**：控制面板[noVNC]使用的端口，国内主机应避免使用80、443、8080等特殊端口。
>>**/root/coolq-data**：用于储存酷Q AIR的目录，插件目录、数据都在这里，需与上文创建的注明可修改的目录一致。
>
>>**QQ**：机器人帐号，其值会自动填入酷Q AIR的QQ账号栏中，酷Q也会储存密码，对自动化有利，此处给的字母是不会自动填入的，因为账号是数字的。
>
>>**可选参数：-d**：不会显示详细的调试信息，仅输出容器ID并挂起，不需要再次手动启动容器。不建议第一次开机器人时使用。

> **一些查看操作**：
> > **systemctl status docker**：查看docker运行状态， 有一个docker-proxy说明正常运行。
> > **netstat -pantu**：查看端口开放情况
 

### 5. 打开阿里云服务器的端口

进入阿里云管理界面，点击实例->网络和安全组->安全组配置->配置规则->手动添加，加入步骤4中的端口，开放对应的端口。

### 6. 登录noVNC
浏览器中输入[服务器外网ip：端口号]，使用VNC密码登录，然后输入账号密码登录qq。
之后按照教程配置机器人。

### 7. 添加应用
从酷q应用社区中查找应用，将cpk文件上传到服务器的/root/coolq-data/app文件夹下。
>酷q社区已经禁止新用户注册，可以加qq群找数据包的cpk文件
