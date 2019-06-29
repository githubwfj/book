### Maven

下载安装包
```
wget http://mirror.bit.edu.cn/apache/maven/maven-3/3.6.1/binaries/apache-maven-3.6.1-bin.tar.gz
```
将maven.tar.gz拷贝/user/local目录下解压
```
sudo tar -zxvf apache-maven-3.6.1-bin.tar.gz -C /usr/local/
```
编辑配置文件，配置环境变量
```
sudo vim /etc/profile 
```

添加如下内容
```
export M2_HOME=/usr/local/apache-maven-3.6.1
export PATH=${M2_HOME}/bin:$PATH
```

配置立刻生效
```
source /etc/profile
```

检查是否安装成功
```
mvn -v
```
