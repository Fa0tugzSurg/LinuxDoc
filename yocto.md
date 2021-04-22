# 使用Yocto构建Qt for ARM

## 构建前准备 

1.环境需求

* 一台Ubuntu16.04 64位计算机系统，硬盘至少100G，内存至少2G,最好4G以上

* 一台基于imx6 cpu的开发板

2.安装Yocto工具需要用到的软件包

```
$sudo apt-get install vim gcc-arm-linux-gnueabihf g++-arm-linux-gnueabihf -y
$sudo apt-get install gawk wget git-core diffstat unzip p7zip-full texinfo -y
$sudo apt-get install gcc-multilib build-essential chrpath libsdl1.2-dev xterm gperf bison curl -y
$sudo apt-get install udisks screen -y
```

安装32位支持库

```
sudo apt-get install g++-multilib zlib1g:i386
```

如果Ubuntu比较老，例如12.04,则安装以下软件

```
sudo apt-get install g++-multilib ia32-libs
```

## 设置Yocto编译环境

```
$mkdir qt5.7 && cd qt5.7
$git clone git://code.qt.io/yocto/meta-boot2qt.git
$cd && mkdir b2qt
$cd b2qt
$~/qt5.7/meta-boot2qt/b2qt-init-build-env init --device imx6dlsabresd
```

## 编译Yocto

```
$export MACHINE=imx6dlsabresd
$source setup-environment.sh imx6dlsabresd
$bitbake b2qt-embedded-qt5-image
```

## 常见问题解决

1. git配置问题，出现如下问题

```
*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'huangfu@ubuntu.(none)')
```

则配置git用户名和邮箱

```
$git config --global user.email "balconystudio@foxmail.com"
$git config --global user.name "hflw"
```
