### Oracle JDK
Oracle JDK 1.8 [链接](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

## 二进制安装
下载二进制安装包
```
wget https://download.oracle.com/otn/java/jdk/8u211-b12/478a62b7d4e34b78b671c754eaaf38ab/jdk-8u211-linux-x64.tar.gz?AuthParam=1560077784_42ac21a9555f4951eed58e2985231cc8
```
在usr目录下建立java安装目录
```
mkdir -p /usr/lib/java
```
将jdk-8u60-linux-x64.tar.gz拷贝到java目录下解压
```
tar -zxvf jdk-8u131-linux-x64.tar.gz -C /usr/lib/java
```
编辑配置文件，配置环境变量
```
vim /etc/profile
```

添加如下内容：JAVA_HOME根据实际目录来
```
#set oracle jdk environment
export JAVA_HOME=/usr/lib/java/jdk1.8.0_131
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
## rpm 安装
下载rpm安装包
```
wget https://download.oracle.com/otn/java/jdk/8u211-b12/478a62b7d4e34b78b671c754eaaf38ab/jdk-8u211-linux-x64.rpm?AuthParam=1560077852_7f7b4dfff4d7f080133d011af966ddbd
```
添加可执行权限
```
chmod +x jdk-8u101-linux-x64.rpm
```
执行rpm命令安装
```
rpm -ivh jdk-8u212-linux-x64.rpm
```
查看是否安装成功
```
java -version

javac -version
```