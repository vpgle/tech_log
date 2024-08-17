---
title: fedora37 update fedora40
date: 2024-08-17 10:46:27
tags: fedora37,fedora40
categories: linux
---

## 思路

因为fedora37的官方repo已不提供，命令行升级的可能性已存在，所以在新硬盘上安装fedora40，把fedora37硬盘挂在到fedora40系统

## 操作

在window系统用官方Fedora Media Writer工具做U盘引导镜像，工具自带下载镜像功能，好用！
 又到了分区环节，37用的分区是/usr, /var, /opt 单独分了100G，这些分区用不完，还占用磁盘空间，这次重新分配

<style>
</style>

| 分区  | 磁盘大小 | 格式  |
| --- | --- | --- |
| /boot/efi | 2G  |     |
| /boot | 20G |     |
| /   | 300G | lvm |
| /home | 300G | lvm |

## 安装完成的一些变更

### 1.登录用的显示管理器用lightdm替换gdm

禁用gdm开机启动

```shell
systemctl disable gdm
```

安装lightdm

```shell
yum search fedora.release
sudo yum groupinstall xfce
sudo yum install xfce4*
```

开机启动

```shell
systemctl enable lightdm.service
```

开启服务

```shell
systemctl start lightdm.service
```

登录时有个问题，选择xfce4会话，密码正确还是会跳回未输入密码的画面，但是先用gnome会话登录成功后注销，再用xfce4会话登录就可以登录成功

在 /etc/pam.d/login 文件行尾添加

```shell
session    required     /lib64/security/pam_limits.so
```

依然没有解决问题

###

### vsftp配置

安装ssh和vsftpd后

确认sshd.service服务文件是否生成

```shell
systemctl list-unit-files | grep ssh
```

开机启动sshd服务

```shell
systemctl enable sshd.service
```

开始sshd服务

```shell
systemctl start sshd.service
```

用nc -nvv IP 22

```shell
nc -nvv IP 22
```

显示 CONNECT SUCCESS 字样即为成功

# 未完待续


