# 妙算机载电脑调教经验

Author：@skyswordx(袁越)  
Date：2025.1.12

## 开机使用方式

要准备一个便携式 HDMI **显示屏**，需要在接电源前先连接 HDMI 显示屏
- ~~一般如果连续显示屏没有 HDMI 信号的话，可能是之前的线把接口搞歪了，只能用之前的线。~~
- 有一台机子实测是 HDMI 接口和电源线的接口之间有点问题，如果插上 HDMI 每一次换一个电源接口试一下

然后按 `F12` 或者 `del` 进 BIOS，然后直接保存退出进入系统

然后要给机子插上网卡
在 ubuntu 里面如果连不上网络，试一下重启网络服务，相关命令如下
```bash
>> sudo service network-manager stop
>> sudo service network-manager restart
```


## 关于刷机

大疆官方 manifold-2: [ubuntu_16.04_iso镜像](https://www.dji.com/cn/manifold-2/downloads)
如果要重装系统，进入 bios 后在 boot 选项页面里面调整配置文件的顺序 (把 UEFI: 开头的放在第一位)

由于 ubuntu16.04 和对应的 ROS1 已停止维护，所以**可能**需要升级系统
- 参考 [manifold 2-c系统升级为18.04-CSDN博客](https://blog.csdn.net/weixin_43568893/article/details/120209869)
	- 实测可以一直升级到 20.04
- 在升级 ubuntu 系统前记得删除 ROS 相关的东西，否则会升级失败


## 新上手刷完机要配置的

远程登录相关
- 可选配置 ssh 登录
	- [当时的参考链接](https://zhuanlan.zhihu.com/p/514679761)

连接网络相关
- 网卡名字奇奇怪怪
	- [当时的参考链接](https://blog.csdn.net/weixin_42409052/article/details/113065704)
	- 更改了网卡命名规则
	- 发现有的机子确实只能连热点

之前用到其他小问题留下的参考链接
- [查看IP地址](https://zhuanlan.zhihu.com/p/81212996)
- [内网穿透](https://www.cpolar.com/blog/ssh-remote-connection-to-ubuntu-system)
- [命令行读取u盘文件](https://blog.csdn.net/weixin_51359215/article/details/120678744)
- [调整终端字体大小](https://blog.csdn.net/qq_30115765/article/details/52623935)

## 未解决的问题

- 发现了无法支持中文，没有中文输入法
- 有的机子，开机即风扇猛转，没有发现更改散热风扇转速的脚本