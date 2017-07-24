# mac编译bison版本低

http://blog.csdn.net/cumt168/article/details/50457962
```
Bison version 2.5 or higher must be installed on the system!
```

安装thrift时，报错：

`Bison version 2.5 or higher must be installed on the system!`
使用brew install bison 安装新版的bison

$ brew list bison
/usr/local/Cellar/bison/3.0.4/bin/bison
/usr/local/Cellar/bison/3.0.4/bin/yacc
/usr/local/Cellar/bison/3.0.4/lib/liby.a
/usr/local/Cellar/bison/3.0.4/share/aclocal/bison-i18n.m4
/usr/local/Cellar/bison/3.0.4/share/bison/ (23 files)
/usr/local/Cellar/bison/3.0.4/share/doc/ (14 files)
/usr/local/Cellar/bison/3.0.4/share/info/bison.info
/usr/local/Cellar/bison/3.0.4/share/man/ (2 files)
已经安装3.0.4版本

但是安装thrift，仍然报错

Bison version 2.5 or higher must be installed on the system!

经查是使用了xcode自带的bison，路径 /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/

解决办法：

首先将bison改名

cd /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/

sudo mv bison bison111

然后新版本的bison复制到路径下

sudo cp /usr/local/Cellar/bison/3.0.4/bin/bison  /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/

再次安装thrift，安装成功。

cd /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/

sudo rm bison

sudo mv bison111 bison

# 缺少openssl/openssl.h

## 现象

```
fatal error: 'openssl/evp.h' file not found
fatal error: 'openssl/openssl.h' file not found
```

## 解决办法
参考这个http://www.cnblogs.com/pengei/p/6625574.html

```Shell
./configure --with-openssl-dir="本机openssl的目录"
//比如我的mac
./configure --with-openssl=/usr/local/opt/openssl
//或者这种办法
./configure LDFLAGS='-L/usr/local/opt/openssl/lib' CPPFLAGS='-I/usr/local/opt/openssl/include'  --prefix=/usr/local

```
## 原因
>MacOS的升级最新版本中不再提供openssl
>官方说明：https://lists.apple.com/archives/macnetworkprog/2015/Jun/msg00025.html
>在配置编译环境的时候手动设置下即可

