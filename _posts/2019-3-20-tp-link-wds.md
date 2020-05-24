配置无线桥接网络，需要设备：路由器1，路由器2，主机


1. 主机无线连接路由器1，将路由器1设置ip地址为192.168.1.1

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/1.png?raw=true)


2. 配置路由器1的基本信息，记录SSID和信道号

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/2.png?raw=true)

3. 路由器1开启DHCP服务

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/3.png?raw=true)

4. 测试主机可以正常联网

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/4.png?raw=true)

5. 主机无线连接路由器2，修改路由器2的ip地址，让路由器1和路由器2在同一个网段，这里修改为192.168.1.2

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/5.png?raw=true)

6. 修改了路由器的ip之后，需要使用新的ip地址重新登陆管理界面

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/6.png?raw=true)

7. 配置路由器2的基本信息，需要与路由器1在相同信道内；开启WDS，点击扫描

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/7.png?raw=true)

8. 在扫描到的无线网中，找到路由器1的SSID，点击连接

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/8.png?raw=true)

9. 查看路由器2的运行状态，WDS状态为成功

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/9.png?raw=true)

10. 此时主机仍然连接路由器2，测试网络，不通

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/10.png?raw=true)

11. 关闭路由器2的DHCP

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/11.png?raw=true)

12. 再次测试网络，可以正常上网

![ip](https://github.com/katsuunhi/katsuunhi.github.io/blob/master/img/wds/12.png?raw=true)