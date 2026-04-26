# NETWORK - SECURITY
网络安全

## 目录
- [命令](#命令)
  - [yum](#yum)
  - [systemctl](#systemctl)
  - [ip](#ip)
  - [hostnamectl](#hostnamectl)
- [课外知识](#课外知识)
  - [Shell](#Shell)
  - [网卡](#网卡)
- [效果展示（图片/截图）](#效果展示图片截图)
- [项目结构](#项目结构)


## 命令 

### yum 
```bash
# 安装 Linux 软件(vim、tree、lrzsz、wget、curl、unzip、net-tools)
yum install -y vim tree lrzsz wget curl unzip net-tools
```

### systemctl
```bash
# 重启网络服务
systemctl restart network

# 关闭防火墙服务
systemctl stop firewalld

# 取消防火墙自启
systemctl disable firewalld
```

### ip
```bash
# 查看网络信息
ip a
```

### hostnamectl
```bash
# 设置该主机名为xxx
hostnamectl set-hostname xxx
```

## 课外知识
### Shell
命令解释器
- **交互式**：输入命令（如 ls ）回车，系统回显信息
- **非交互式**：#!/bin/bash echo "Hello World" (打印 Hello World) 或者 .sh 后缀可执行文件

### 网卡
配置文件 /etc/sysconfig/network-scripts/ifcfg-ens33
```bash
TYPE="Ethernet"
PROXY_METHOD="none"
BROWSER_ONLY="no"
BOOTPROTO="dhcp" # auto / static
DEFROUTE="yes"
IPV4_FAILURE_FATAL="no"
IPV6INIT="yes"
IPV6_AUTOCONF="yes"
IPV6_DEFROUTE="yes"
IPV6_FAILURE_FATAL="no"
IPV6_ADDR_GEN_MODE="stable-privacy"
NAME="ens33"
UUID="eb15b087-f7ef-47e2-a9cd-f256200ac212" #删去
DEVICE="ens33" #删去
ONBOOT="yes"
IPADDR = 192.168.88.128 #设置静态ip
NETMASK = 255.255.255.0 #设置子网掩码
GATEWAY = 192.168.88.2 #设置网关
DNS1 = 192.168.88.2 #设置DNS，一般与网关相同
```

- **物理服务器**：< DELL： em1、em2、em3、em4 >
- **云服务器**：<  阿里云：eth0 >

## 效果展示（图片/截图）
- **项目 Logo（可选）**：

![Logo](./assets/logo.png)

- **截图/动图（推荐放到 `assets/` 目录）**：

![截图说明：<这里写一句图注>](./assets/screenshot-1.png)

- **外链图片（可选）**：

![截图说明：<图注>](https://example.com/screenshot.png)

- **可控尺寸（兼容性写法，GitHub 支持）**：

<img src="./assets/screenshot-2.png" alt="截图说明：<图注>" width="720" />

## 项目结构

```text
.
├─ <dir_or_file_1>  # <说明>
├─ <dir_or_file_2>  # <说明>
└─ README.md
```