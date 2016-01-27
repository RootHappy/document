### 安装 JDK
- 环境：Ubuntu 14.04 , jdk 7
	- 解压jdk文件（～/someInstallPackage/jdk-7u21-linux-x64.tar.gz）
	- tar xzvf ～/someInstallPackage/jdk-7u21-linux-x64.tar.gz
	- 环境变量配置

    ```
    #/etc/bash.bashrcSS

    JAVA_HOME=/app/jdk1.7.0_21
    PATH=$PATH:$JAVA_HOME/bin
    CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

    export JAVA_HOME
    export PATH
    export CLASSPATh
    ```

### 安装和配置git
- 安装环境：ubuntu 14.04
	- sudo apt-get update
	- sudo apt-get install git
- 配置个人信息
	- git config --global user.name developer_name
	- git config --glocal user.email developer_email
- 生成ssh秘钥
	- ssh-keygen -t rsa -C "wangyunlong786@163.com"

### 安装配置gradle
- 安装环境 ubuntu 14.04
- 解压文件（～/someInstallPackage/gradle-1.12-bin.zip）
	- unzip ～/someInstallPackage/gradle-1.12-bin.zip
- 配置环境变量

    ```
    GRADLE_HOME=/app/gradle-1.12
    PATH=$PATH:$GRADLE_HOME/bin
    export PATH
    ```

### 安装配置 Thrift

    ```shell
    #configure thrift 0.9.0
    sudo apt-get install libboost-dev libboost-test-dev libboost-program-options-dev libevent-dev automake libtool flex bison pkg-config g++ libssl-dev

    sudo cp -r thrift-0.9.0 /usr/local/
    cd /usr/local/thrift-0.9.0
    sudo ./configure --with-qt4=no && sudo make &&  sudo make install
    ```



### 安装配置TOMCAT
- 安装环境 ubuntu 14.04
- 解压文件（～/someInstallPackagetomcat-7.0.52-utf8.tar.gz）
	- tar xzvf ～/someInstallPackagetomcat-7.0.52-utf8.tar.gz
- 启动tomcat