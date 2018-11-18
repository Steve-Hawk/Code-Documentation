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

## C++ Style
- 在类或者模版类的定义时，如果成员函数的语法块比较小，就直接在声明的地方完整写出来，使用内联函数的形式
