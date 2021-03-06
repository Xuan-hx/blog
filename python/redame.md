## 基于 Python 进行 App 服务器端开发

    根据第 3 节的介绍，开发环境需要安装如下软件：Python 3、Tornado、MySQL 和 SQLAlchemy。

    ### 安装 Python 3.6.2

    CentOS 7.2 操作系统自带的 Python 版本为 2.7.5，本小册将以 Python 3.6.2 的版本进行讲解。即安装完 Python 3.6.2 后，系统上同时存在 Python 2.7.5 和 Python 3.6.2 两个版本。...

## 安装依赖包

    yum -y groupinstall "Development tools"
    yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel...

## 下载 Python 3.6.2

    wget https://www.python.org/ftp/python/3.6.2/Python-3.6.2.tar.xz

    创建安装目录

        mkdir /usr/local/python3

    由于 Python 3.6.2 的编译需要编译环境，故需安装 gcc。

        yum -y install gcc

    安装 Python 3.6.2

        解压 Python 3.6.2 并安装在 /usr/local/python3 目录下。

        tar -xvJf  Python-3.6.2.tar.xz
        cd Python-3.6.2
        ./configure --prefix=/usr/local/python3
        make && make install...

    创建软连

        ln -s /usr/local/python3/bin/python3 /usr/bin/python3
        ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3

### 安装 Tornado

        CentOS 下还无法直接使用 yum install tornado，但可以使用 pip 安装 Tornado。先执行 pip3 install --upgrade pip 命令升级 pip，再执行 pip3 install tornado 命令安装 Tornado。...

    测试 Tornado 是否安装成功：
        执行 import tornado 没有报错，表示 Tornado 已安装成功。

### 安装 MySQL

        yum install mysql-devel
        wget http://dev.mysql.com/get/mysql-community-release-el7-5.noarch.rpm
        rpm -ivh mysql-community-release-el7-5.noarch.rpm
        yum -y install mysql-community-server
        pip3 install mysqlclient
        service mysqld restart...

    测试 MySQL 安装是否成功：

        systemctl status mysqld.service

### 安装 SQLAlchemy

        使用 pip3 安装 SQLAlchemy：

            pip3 install SQLAlchemy

        测试 SQLAlchemy 是否安装成功，服务器端依次输入如下命令。

            python3
            import sqlalchemy

        没有报错，证明 SQLAlchemy 已安装成功。
