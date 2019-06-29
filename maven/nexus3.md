### nexus
下载安装包
```
wget https://sonatype-download.global.ssl.fastly.net/repository/repositoryManager/3/nexus-3.16.2-01-unix.tar.gz
```
将nexus.tar.gz拷贝/opt/nexus 目录下解压
```
mkdir /opt/nexus

tar -zxvf nexus-3.16.2-01-unix.tar.gz -C /opt/nexus
```
启动
```
cd /opt/nexus/nexus-3.16.2-01/bin

./nexus start

./opt/nexus/nexus-3.16.2-01/bin/nexus start

# 启动，打印日志
./nexus run

# 查看状态
ps -aux | grep nexus
```
修改配置
[官方文档](https://help.sonatype.com/repomanager3/installation/configuring-the-runtime-environment)
[官网文档](https://help.sonatype.com/repomanager3/system-requirements#SystemRequirements-Memory)

```
cd /opt/nexus/nexus-3.16.2-01/bin
vim nexus.vmoptions

# 测试最低配置 1G
-Xms512M
-Xmx512M
-XX:MaxDirectMemorySize=1G
```

防火墙
```
firewall-cmd --get-active-zones
firewall-cmd --zone=public --add-port=8081/tcp --permanent
firewall-cmd --reload
firewall-cmd --query-port=8081/tcp
```

访问
```
http://localhost:8081
默认端口:8081
账号:admin
密码:admin123
```

## 角色及权限管理
```
# 增加 Developer 开发者角色
1.全部读取权限
2.maven-releases 的上传权限
3.maven-snapshots 的上传权限

# 增加 Maintainer  维护者角色
1.删除权限以外的所有权限
```