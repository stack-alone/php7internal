讨论总结：
# 一、 环境的配置，php安装脚本：
``` 
 #!/bin/bash
 mkdir /usr/local/php7.1.0
 wget https://www.php.net/distributions/php-7.1.0.tar.gz
 tar -xzvf php-7.1.0.tar.gz
 cd php-7.1.0
```
# 下面这条命令的作用是：不检查编译环境是否完整，强行生成Makefile.这一步可有可无，
``` 
./buildconf --force
./configure --prefix=/usr/local/php7.1.0/ --enable-fpm --enable-debug
``` 
# 下面这条命令运行时间较长，请耐心等待，大概20分钟左右
``` 
make
make install
``` 
  二、源码跟目录
  ``` 
 appveyor：里面都是一些bat脚本，为PHP的Windows构建提供持续集成。

build：linux下编译相关的目录。

ext：即extension，php下的扩展包源码，如我们熟知的mysqli、gd、curl、mbstring等等。

main：为php的主要代码，主要是输入/输出、web通信，以及php框架初始化操作等，比如fastcgi协议的解析、扩展的加载、php配置的解析等工作都是由它来完成的。

netware：网络目录，以前的版本没有此目录，里面有2个文件sendmail_nw.h、start.c，分别定义socket通信所需要的头文件和具体实现。

pear：扩展包目录，PEAR即：PHP Extension and Application Repository。它是一个PHP扩展及应用的一个代码仓库，简单地说，pear就是PHP的cpan。具体用户可以查阅相关资料。

sapi：是php的应用接口层。我们可以在不同环境中应用php，比如命令行下、web环境中、嵌入其他应用。为此，php提供一个SAPI层以适配不同的应用环境，SAPI可以认为是php的宿主环境，也是整个php框架最外层的一部分，它主要负责php框架的初始化工作。经常用到的3个SAPI是cgi、cli、fpm。

scripts：脚本目录。

tests：测试目录，Helper for simple tests to check return-value。

travis：compile.sh

TSRM：线程安全相关的实现。

win32：Windows下编译PHP有关的脚本。

Zend：是php解析器的主要实现，即ZendVM，它是php语言的核心实现，php代码的解释、执行就是由zend完成的。它介于应用与实际计算机中间，主要分为：编译器、执行器两个部分。其中编译器负责将php代码解释为执行器可以识别的指令，执行器负责执行指令，ZendVM相当于java中的JVM，他们都是抽象出来的虚拟计算机。
``` 
  
