### Apache Archiva
下载安装包
```
wget http://mirror.bit.edu.cn/apache/archiva/2.2.4/binaries/apache-archiva-2.2.4-bin.tar.gz
```
将nexus.tar.gz拷贝/opt 目录下解压
```
tar -zxvf apache-archiva-2.2.4-bin.tar.gz -C /opt/
```
修改配置文件
```
cd /opt/apache-archiva-2.2.4

vim conf/jetty.xml
```
启动
```
cd /opt/apache-archiva-2.2.4

./bin/archiva console

# 查看状态
ps -aux | grep archiva
```
创建一个链接
```
ln -sf /opt/apache-archiva-2.2.4/bin/archiva /etc/init.d/archiva
```
命令
```
# 启动
service archiva start

service archiva stop

service archiva restart
```

访问
```
http://localhost:8080
默认端口:8080
账号:admin
密码:admin123

```