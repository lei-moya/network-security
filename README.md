# NETWORK - SECURITY
网络安全

## 目录
- [专业术语](#专业术语)
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

## 专业术语

### 漏洞
（vulnerability）硬件、软件、协议等存在的安全缺陷

### POC
（Proof of Concept）证明漏洞存在的代码

### exp
（Exploit，攻击目的）利用代码

### payload
攻击载荷

### 0day
通用产品已经被发现（未公开），但官方未发布补丁或修复方法的漏洞

### 1day
POC和EXP已公开，但多数人未修复的漏洞

### Nday
已发布官方补丁，且时间久远的漏洞

### 漏扫
基于数据库对漏洞进行自动化扫描

### 补丁
（patch）漏洞的修复程序

### 渗透
（penetration）黑客入侵网站或计算机系统，获取控制权限的过程

### 渗透测试
（penetration test）用黑客入侵的方式对系统进行安全测试，目的是找出和修复安全漏洞，在这个过程中不会影响系统的正常运行，也不会破坏数据

### 木马
（Trojan horse）隐藏在计算机中的恶意程序

### 病毒
（Virus）恶意代码或程序

### 肉鸡
已经被黑客获得控制权限的机器，可能是个人电脑，也可能是企业或政府单位的服务器，通常情况下因为使用者并不知道已经被入侵，所以黑客可以长期获得权限和控制

### 抓鸡
利用出现概率高的漏洞，使用自动化方式获取肉鸡的行为

### 跳板机
黑客为了防止被追溯和识别身份，一般都不会用自己的电脑发起攻击，而是利用获取的肉鸡来攻击其他目标，这个肉鸡就充当一个跳板的角色

### DDos
（Distributed Denial of Service，分布式拒绝服务攻击）发起大量恶意请求，导致正常用户无法访问

### 中间人攻击
（Man-in-the-Middle Attack，MITM攻击)运行中间服务器，拦截并篡改数据

### 网络钓鱼
钓鱼网站指冒充的网站，用来窃取用户的账号密码

### shell
一种命令执行工具，可以对计算机进行控制
- **webshell**：除asp、php、jsp之外的web代码文件，通过这些代码文件可以执行任意命令，对计算机做任意操作
  - 小马
  - 大马
- **Getshell**：获得命令执行环境的操作

### 拿站
得到一个网站的最高权限，即得到后台和管理员的名字的密码

### 拖库（脱裤）
网站被入侵以后，黑客把全部数据导出，窃取到了数据文件
- **裤子**：数据文件

### 撞库
用获得的裤子去批量登录其他的网站

### 旁站入侵
入侵同服务器的其他网站

### 横向移动
攻击者入侵一台服务器成功以后，基于内部网络，继续入侵同网段的其他机器

### 代理
（Proxy）帮我们发起网络请求的一台服务器

### VPN
（Virtual Private Network）

### 蜜罐
（Honeypot）吸引攻击者攻击的伪装系统，用来实现溯源和反制

### 沙箱
（sandbox）一种按照安全策略限制程序行为的执行环境，就算有恶意代码，也只能影响沙箱环境而不影响到操作系统

### 靶场
模拟的有漏洞的环境（网站、容器、操作系统）
- **web综合靶场**
- **web专用靶场**
- **漏洞复现靶场**
- **操作系统靶场**
- **CTF靶场**

### 堡垒机
运维用跳板机（jumpserver），运维审计系统

### WAF
（Web Application Firewall，web应用防火墙）对http/https的流量内容进行分析，拦截恶意攻击行为

### APT攻击
（Advanced Persistent Threat）高级可持续威胁攻击，指某组织在网络上特定对象展开的持续有效的攻击活动

### 护网（HVV）
国家组织牵头组织事业单位、国企单位、名企单位等开展攻防两方的网络安全演习

### CTF
Capture The Flag夺旗赛

### CVE
（Common Vulnerabilities and Exposures，通用漏洞披露）

### CNVD
- **国家信息安全漏洞共享平台**
- **国家计算机应急响应中心 CNCERT维护**

### 应急响应
一个公司为了应对各种安全事件所做的准备和事后采取的措施

### SRC
（Security Response Center，企业的应急响应中心）
- **公益SRC**

### 网络空间测绘
- **网络空间资源收录**
- **网络空间搜索引擎**

### ATT&CK
（Adversarial Tactics, Techniques, and Common Knowledge，对抗战术、技术和通用知识，俗称攻击者战术的知识库）
- **风险分析模型**：收集威胁情报，模拟APT攻击

### 逆向
（Reverse）把程序还原为源代码，分析程序的运行过程

### DevOps
（Development+Operations）开发测试运维一体化

### CICD
- **持续集成（Continuous Integration）**
- **持续交付（Continuous Delivery）**
- **持续部署（Continuous Deployment）**

### DevSecOps
（Development+Security+Operations，安全开发与运维）

### 等保
网络安全等级保护，要求相关行业的单位和公司的信息系统必须进行定级，然后在公安机关备案，然后建设整改，然后由测评机构评级，并且持续维护和监督

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