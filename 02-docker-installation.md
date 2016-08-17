## 第 2 章 Docker 环境安装

![Docker Toolbox](http://play-docker.oss-cn-hangzhou.aliyuncs.com/images/docker-toolbox.png)

### 第 1 章 Docker安装与配置
我们将分别讲述如何在Linux、Windows以及Mac OS中安装Docker。

Docker Toolbox是一款让你简单快速的安装部署Docker环境的安装套件。

#### Linux下安装Docker
内核要求
以Ubuntu为例，支持的版本，以Ubuntu 14.04 为例安装

安装前检查：
1、内核版本
  $ uname -a
2、检查Device Mapper
  $ ls -l /sys/class/misc/device-mapper

如果这两个条件有不满足的情况，那么我们就要升级内核版本。

Ubuntu中安装Docker的方式
1、安装Ubuntu维护的版本
  $ sudo apt-get install -y docker.io
  $ source /etc/bash_completion.d/docker.io
2、安装Docker维护的版本
  1. 检查APT的HTTPS支持情况：查看/usr/lib/apt/methods/https文件是否存在
    如果不存在，运行安装命令
    $ apt-get update
    $ apt-get install -y apt-transport-https
  2. 添加Docker的APT仓库
    $ echo dev https://get.docker.com/ubuntu docker main > /etc/apt/sources.list.d/docker.list
  3. 添加仓库的key
  4. 安装Docker
3、简易安装方式
  1. $ duso apt-get install -y curl
  2. $ curl -sSL https://get.docker.com/ubuntu/ | sudo sh

查看Docker安装的版本：
  $ docker version
  $ 1.10.1
  这是目前Docker最新的版本
  $ docker info

不使用root账户来运行docker
  1. $ sudo groupadd docker
  2. $ sudo gpasswd -a ${USER} docker
  3. $ sudo service docker restart



#### 在Windows/OS X下安装Docker

* Linux容器技术
* 操作系统级别的虚拟化
* 依赖于Linux内容的Namespace和Cgroups

Toolbox简介：
包含：
1. Boot2Docker Linux ISO / 轻量级的Linux发行版，为Docker定制
2. Virtualbox / VM
3. MSYS-git / Docker客户端
4. 管理工具

Docker的守护进程需要通过Toolbox的虚拟机来承载

安装Toolbox
支持Windows 7/8，更早的版本，但不推荐
支持OS X

打开官网
下载
双击安装文件
根据向导提示安装
需要重启系统么？

点击Toolbox start
自动打开shell界面，启动虚拟机，使用docker用户名登录
查看docker版本
运行docker容器

到这，我们已经成功的在windows上通过Toolbox搭建了Docker的运行环境，并且运行了一个Docker容器。
Windows对Docker的支持还比较原始，从理论上来说，Docker目前并不能支持Windows应用的部署，但MS对Docker给予了厚望

#### 在OS X中安装Docker
首先我们来回顾一下Docker需要的运行环境，Docker是基于Linux容器的一门技术，它提供了操作系统级别的虚拟化，而且依赖于Linux内核的Namespace和Cgroups等特性。
所以Docker需要的Linux的运行环境，而在OS X中并不具备这样的运行环境，所以Docker并不能直接的运行在OS X中。

Toolbox是什么？

两张图对比

系统要求：OS X 10.6 "Snow Leopard"之后的版本

下载并安装Toolbox，一键式的安装包

lanuchpad中多了两个图标，Toolbox的启动过程：
1. 打开命令行窗口
2. 建立 $HOME/.boot2docker 目录
3. 创建VirtualBox ISO
4. 启动虚拟机并运行Docker守护进程

Toolbox启动时有哪些命令：

运行容器

总结：
虽然可以在Windows/Mac OS上可以搭建Docker的运行环境，但这个环境一般只是用于我们做开发或者测试之用，而不用于正在的生成部署。
