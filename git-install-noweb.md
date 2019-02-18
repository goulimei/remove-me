###无网络环境下，git源码文件安装

**说明**  

本文针对linux的Redhat系列(FedoraCore,RHEL,CentOS),ubuntu采用apt-get,这里略过。

**目前已测试过：**  

- centos7(kernel-release:3.10.0-229.el7.x86_64);  
- 中标麒麟3.2(kernel-release：2.6.32-220.7.1.1.ky3.2.x86_64);  
- 其中centos7自带git版本为:git version 1.8.3.1


####1.解压缩git源码文件

    tar -xzvf cd git-2.16.2.tar.gz 
    cd git-2.16.2


####2.编译git源文件

    ####  由于git依赖的库很多,可以先碰运气,安装试试  #### 
    make configure
    ./configure --prefix=/usr
    
    ####  编译所有  ####
    make all doc
    
    ####  若无错误,恭喜你,直接进入步骤3  ####
    ####  但90%都会报错,例如下面的示例  #### 
    ####  sample ####
    ASCIIDOC git-log.html
    /bin/sh:行1: asciidoc: 未找到命令
    make[1]: *** [git-log.html] 错误 127
    make[1]: 离开目录“/home/gis/git-2.16.2/Documentation”
    make: *** [doc] 错误 2
    
    ####  此时请跳到步骤4,(缺哪个第三方库，编译和安装哪个)  ####
    ####  完成后,再返回步骤2  ####

####3.安装git

    su
    make install install-doc install-man install-html
    ####  验证git安装成功  ####
    git --version
    git version 2.16.2   // git安装成功

####4.编译、安装git依赖的第三方库(需要时)  
#####4.1 安装asciidoc
  
    tar -xzvf asciidoc-8.6.9.tar.gz
	cd asciidoc-8.6.9
	./configure --prefix=/usr
	su
	make && make install
[下载asciidoc](!https://pan.baidu.com/s/1E0fki6RHq-HUOpuHUoG3iA)	

#####4.2 安装xmlto
		
    tar -xzvf xmlto-0.0.28.tar.gz
    cd xmlto-0.0.28
    ./configure --prefix=/usr
    su
    make && make install
[下载xmlto-0.0.28](!https://pan.baidu.com/s/1tKxLWOWd8UBf8cGU2QjdLQ)	

#####4.3 安装zlib
		
    tar -xzvf zlib-1.2.8.tar.gz
    cd zlib-1.2.8
    ./configure --prefix=/usr
    su
    make && make install
[下载zlib-1.2.8](!https://pan.baidu.com/s/1tOzcfjoCiN54-XQIXhBU2A)			

#####4.4 安装perl

    tar -xzvf perl-5.22.1.tar.gz
    cd perl-5.22.1
    ./configure.gnu --prefix=/usr
    su		
    make && make install
[下载zlib-1.2.8](!https://pan.baidu.com/s/1uhzzowaFdOKt5AywzRlaIA)			

#####4.5 安装openssl
		
    tar -xzvf openssl-1.0.2.tar.gz
    cd openssl-1.0.2
    ./configure --prefix=/usr
    su
    make && make install
[下载zlib-1.2.8](!https://pan.baidu.com/s/1JYTkjiUxO0awSFbtSA6kWQ)	