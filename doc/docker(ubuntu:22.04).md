# 创建docker(ubuntu:22.04)编译镜像

### 1. docker的安装和相关指令自行网上查询
### 2. docker下拉最新ubuntu镜像（ubuntu:22.04）
```bash
docker pull ubuntu
```
### 3. docker创建并且进入容器（本人选择docker网络模式是host）
```bash
docker run -it --network=host --name ubuntu ubuntu:latest
```
### 4. 更新apt源
```bash
apt uopdate
```
### 5. 安装sudo
```bash
apt install sudo
```
### 6.安装依赖工具
```bash
sudo apt install -y pkg-config build-essential ninja-build automake autoconf libtool wget curl git gcc libssl-dev bc slib squashfs-tools android-sdk-libsparse-utils jq python3-distutils scons parallel tree python3-dev python3-pip device-tree-compiler ssh cpio fakeroot libncurses5 flex bison libncurses5-dev genext2fs rsync unzip dosfstools mtools tcl openssh-client cmake
```
### 7.安装dialog
```bash
apt install dialog
```
### 8.安装libssl1.1
```bash
wget http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2.19_amd64.deb
sudo dpkg -i libssl1.1_1.1.1f-1ubuntu2.19_amd64.deb
```
### 9.获取sdk
```bash
git clone https://github.com/milkv-duo/duo-buildroot-sdk.git --depth=1
```

### 10.一键编译（过程大概半个小时）
```bash
cd duo-buildroot-sdk/
./build_milkv.sh
```

### 11.恭喜你编译成功，编译生成的镜像文件在out目录下！
