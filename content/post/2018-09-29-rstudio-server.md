---
title: Rstudio server安装脚本
author: ~
date: '2018-09-29'
slug: rstudio-server
categories: [R]
tags: [Rstudio server]
---
# Rstudio服务器安装脚本

	# 安装 epel源
	 yum -y install epel-release
	 # 更新
	 yum update
	 # 获取R的安装包
	 wget https://cran.r-project.org/src/base/R-3/R-3.3.2.tar.gz
	 tar zxvf R-3.3.2.tar.gz
	 cd R-3.3.2.tar.gz
	 # 安装gcc编译器
	 yum install glibc-headers gcc-c++
	 # 安装Fortran编译器
	 yum install gcc-gfortran
	 # 安装
	 yum install readline-devel
	 # 安装
	 yum install libXt-devel
	 # 安装
	 ./configure --with-readline=no --with-x=no
	 make
	 make install
	 
	# 安装 r
	# yum install r-base;
	# 安装r-studio
	wget https://download2.rstudio.org/rstudio-server-rhel-1.0.136-x86_64.rpm;
	sudo yum install --nogpgcheck rstudio-server-rhel-1.0.136-x86_64.rpm;
	# 检验 rstudio-server是否成功安装
	rstudio-server verify-installation
	# 开放端口 8787
	iptables -I INPUT -p tcp --dport 8787 -j ACCEPT;
	# 启动rstudio
	rstudio-server start

#### 配置文件`rsession.conf`和`rserver.conf`
在`rsession.conf`文件中添加

	
	rsession-which-r=/usr/local/bin/R
	
在`rserver.conf`中添加
	
	#改变端口
	www-port=80
	# 改变ip地址
	www-address=127.0.0.1
	
编译环境

	yum -y install gcc 
	yum install glibc-headers 
	yum install gcc-c++ 
	yum install gcc-gfortran 
	yum install readline-devel 
	yum install libXt-devel
	
#### 安装问题
1. configure: error: zlib library and headers are required

		yum -y install bzip2-devel 
		
		yum install R
		
#### 安装完所有环境之后，可以直接用指令安装
	yum install R

#### 启动指令

    iptables -I INPUT -p tcp --dport 8787 -j ACCEPT;
    sudo rstudio-server start;