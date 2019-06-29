### open JDK
open JDK [连接](http://openjdk.java.net/install/)

open JDK 1.8下载 [链接](http://jdk.java.net/java-se-ri/8)

## yum 安装
```
# Java Runtime Environment Java 运行时环境
yum install java-1.8.0-openjdk
# Java 开发套件
yum install java-1.8.0-openjdk-devel
```
## APT 安装
```
# Java Runtime Environment Java 运行时环境
sudo apt-get install openjdk-8-jre
# Java 开发套件
sudo apt-get install openjdk-8-jdk
```

## 二进制安装
下载二进制安装包
```
# Oracle二进制代码许可下的RI二进制文件
wget https://download.java.net/openjdk/jdk8u40/ri/jdk_ri-8u40-b25-linux-x64-10_feb_2015.tar.gz

# RI二进制文件（版本1.8.0_40-b25）在GNU通用公共许可证版本2下
wget https://download.java.net/openjdk/jdk8u40/ri/openjdk-8u40-b25-linux-x64-10_feb_2015.tar.gz
```
在usr目录下建立java安装目录
```
mkdir -p /usr/lib/java
```
将jdk-8u60-linux-x64.tar.gz拷贝到java目录下解压
```
tar -zxvf jdk_ri-8u40-b25-linux-x64-10_feb_2015.tar.gz -C /usr/lib/java

tar -zxvf openjdk-8u40-b25-linux-x64-10_feb_2015.tar.gz -C /usr/lib/java
```
编辑配置文件，配置环境变量
```
vim /etc/profile
```

添加如下内容：JAVA_HOME根据实际目录来
```
# set oracle jdk environment
export JAVA_HOME=/usr/lib/java/java-se-8u40-ri
export CLASSPATH=.:${JAVA_HOME}/lib:${JAVA_HOME}/jre/lib
export PATH=${JAVA_HOME}/bin:$PATH
```

配置立刻生效
```
source /etc/profile
```

检查是否安装成功
```
java -version
javac -version
```