# 在Milkv-Duo上运行ArchLinux系统部分问题及解决方案

本人参照此篇博客编译archlinux：https://community.milkv.io/t/arch-linux-on-milkv-duo-milkv-duo-arch-linux/329

*ps：本篇说明主要分享一些跟随该教程可能会出现的问题～*



## 本地挂载img
### 问题描述

进行以下操作
```bash 
sudo losetup -P loop18 /path/to/duo-buildroot-sdk/install/soc_cv1800b_milkv_duo_sd/milkv-duo.img
```

终端报错
```bash
losetup: 不适用的选项 -- p
```

### 解决方案
安装分区同步工具kpartx
```bash
sudo apt install kpartx
```

分区同步
```bash
sudo kpartx <image> 
```

挂载rootf（?是对应的loop）
```bash
sudo mount /dev/mapper/loop?p2 /mnt/duo-rootf
```

挂载成功，进入/mnt/duo-rootf进行后续操作


## 下载软件包
### 问题描述
wget软件包
```bash
cd /mnt/duo-rootfs/root
wget https://mirror.iscas.ac.cn/archriscv/repo/extra/lrzsz-0.12.20-8-riscv64.pkg.tar.zst
```
软件包获取404
```bash
已发出 HTTP 请求，正在等待回应... 404 Not Found
错误 404：Not Found。
```

### 解决方案
去[软件仓库](https://mirror.iscas.ac.cn/archriscv/repo/)查找获取最新版本的软件（可用ctrl+f查找搜索）

---
注：此教程没有解决USB虚拟以太网，所以开发板不会与主机进行以太网通信，如需要解决USB虚拟以太网，可参考[评论区补充](https://community.milkv.io/t/arch-linux-on-milkv-duo-milkv-duo-arch-linux/329/7)。若无法解决，社区的大佬也有编译好的[img](https://xyzdims.com/3d-printers/misc-hardware-notes/iot-milk-v-duo-risc-v-esbc-running-linux/#References:~:text=0%22%20%3E%3E%20/etc/fstab-,ArchLinux%20Disk%20Image,-I%20followed%20this)可供使用~