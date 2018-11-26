# Techniques & Trickies in coding 
---
## 可用于改进数值计算精度工具库 GNU Multiple Precision Arithmetic Library,GNU MPFR Library:

- [GMP](https://www.gmplib.org/)
- [MPFR](http://www.mpfr.org/)

---

## Macports VS Homebrew
### 共同点：
  - 都是MacOS平台下软件包的管理工具，都类似与Linux系统下的 apt-get yum dnf等下载工具
### 建议：
  - 由于MacOS系统下已经自带有Ruby的安装工具，MacOS系统下的Homebrew比较简单，参考官网上的安装教程就可以；
  - 对于科学计算建议使用Homebrew，识别系统自身的软件包未必是一件坏事，而且用Macports安装的软件（尤其是科学计算方面的软件）经常会出现build的问题；
  - 而且Homebrew下软件的管理更加方便，一方面通过Homebrew安装的软件在一个文件里面，系统识别的终端启动软件的alias名字在另一个文件夹里面，更加方便管理；
  - brew/science -> brewsci/science
---

## Mac开启Proxies时的问题：
  - Network选项下会自动配置Proxy代理设置，如果遇到cannot connet to the server的问题，取消勾选所有的建立的Proxies选项，包括Http & Https；
---

## 服务器上无root权限安装软件与常用库
### 方法
#### 1. 源码编译
- 适用范围 ： 依赖环境包较小，安装过程中的编译命令比较简单
---
#### 2. 使用 Linuxbrew
- 是一个类似于MacOS系统上的包管理安装工具，可以不受系统root权限的限制安装一些Linux和MacOS系统通用的软件，如 ：VIM, GCC等

- 问题 ： 包的管理方式比较复杂，而且会覆盖掉服务器原有的生态环境下的一些库于编译环境，需要在```.bash_profile```中设置环境变量的具体位置路径，对一些Linux系统的包的识别较差，不加区分的安装一些库以及编译环境（Ruby大坑）

- 适用对象，VIM的安装比较方便（==适用于服务器上没有图形界面权限的用户，定制VIM显示方式，便于代码阅读与修改==）
- 使用方式：（基本与MacOS下的使用方式相同）

参考 [Linuxbrew主页说明](http://linuxbrew.sh/)
```(shell)
$ git clone https://github.com/Linuxbrew/brew.git ~/.linuxbrew

$ export PATH="$HOME/.linuxbrew/bin:$PATH"

$ export MANPATH="$(brew --prefix)/share/man:$MANPATH"
$ export INFOPATH="$(brew --prefix)/share/info:$INFOPATH"
```

> 最好在不用一些Linuxbrew安装的库文件的时候，把```.bash_profile```中的路径设置注释掉，例如只使用VIM的情况下时，只需要定义别名的方式使用```VIM```即可

---
#### 3. 使用yumdownloader管理依赖环境

参考[这篇帖子](https://stackoverflow.com/questions/36651091/how-to-install-packages-in-linux-centos-without-root-user-with-automatic-depen)
- 可以像```yum install```的方式安装Linux的软件，且软件仓库比较全面

- 安装大量的软件是需要每一个都做相同的操作，不方便（虽然可以用ShellScript解决）

- 适用于解决一些Linux下如Python-devel,Ruby-devel等的头文件库的安装问题

- 使用简介：(最好查找全面软件的名字)

```(shell)
$ yum search [packagename]
$ yumdownloader --destdir=\path\to\yours [packagename]
$ rpm2cpio x.rpm > x.cpio
$ cpio -id < x.cpio
```
- 在上面的操作完成后，在最后一步执行的文件夹内会出现类似Linux系统文件的 ```/usr```文件夹，安装的相关库以及编译系统与Linux的管理方式大致相同

- 使用这些软件以及库文件时，需要导出到```.bash_profile```的环境变量中
---
### 总结
- 虽然没有Root权限装软件以及设置相关的编译环境比较复杂，但是有效的防止了一些用户不当的操作可能会对服务器自身带来的损害；

- 在使用过程中，切记需要注意到系统自身环境变量会被覆盖的问题；

- 建议在```.bash_profile```文件下面用注释的方式设置多组用户层级下的环境变量名称，便于随时切换与修改；
---
## C++ Style
- 在类或者模版类的定义时，如果成员函数的语法块比较小，就直接在声明的地方完整写出来，使用内联函数的形式
