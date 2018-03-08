---
title: archlinux.md
comments: true
date: 2018-03-08 10:55:38
description:
categories: 
-operation
-interest
tags: 
-linux
---
# archlinux安装与配置

## archlinux安装

```shell
#u盘启动后
wifi-memu # 连接网络
mount /dev/sda1 /mnt
mkdir -p /mnt/home
mount /dev/sda2 /mnt/home
vi /ect/pacman.d/mirrorlist # 修改中国镜像源,如163.com
pacstrap -i /mnt base base-devel
genfstab -U /mnt >> /mnt/etc/fstab #生成挂载文件fstab
```

## archlinux 初步配置

```shell
arch-chroot /mnt /bin/bash #切换到archlinux
```

* 本地语言

```shell
vi /etc/locale.gen
    en_US.UTF-8 UTF-8
    zh_CN.UTF-8 UTF-8

locale-gen #生效
echo LANG=en_US.UTF-8 > /etc/locale.conf
```

* 时区

```shell
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
或
tzselect #按提示选择时区

hwclock --systohc --utc #设置硬件时间
```

* grub引导系统

```shell
pacman -S grub efibootmgr # 支持grub和EFI，可只选grup
grub-install --target=i386-pc --recheck --debug /dev/sda
grup-mkconfig -o /boot/grub/grub.cfg
```

* 网络配置

```shell
systemctl enable dhcpcd.service #有线
pacman -S iw wpa_supplicant dialog #无线
```
