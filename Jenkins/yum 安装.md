# Jenkins
[Jenkins](https://jenkins.io/download/)

[文档](https://wiki.jenkins.io/display/JENKINS/Installing+Jenkins+on+Red+Hat+distributions) 

#### Jenkins的RedHat Linux RPM包
要使用此存储库，请运行以下命令：
```
# LTS version
sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo

sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
```
安装
```
sudo yum install jenkins
```

修改配置
```
vim /etc/sysconfig/jenkins

# 修改端口
JENKINS_PORT="7070"
```
命令
```
# 启动
sudo service jenkins start
# 停止
sudo service jenkins stop
# 重启
sudo service jenkins restart
# 检查状态
sudo chkconfig jenkins on
```

配置防火墙
```
firewall-cmd --get-active-zones
firewall-cmd --zone=public --add-port=7070/tcp --permanent
firewall-cmd --reload
firewall-cmd --query-port=7070/tcp
```

查看初始化密码
```
cat /var/lib/jenkins/secrets/initialAdminPassword

cbe9fac430834c87ad119bc468d7a67b

admin
admin123

root
root123
```

删除
```
service jenkins stop
yum clean all
yum -y remove jenkins

find / -name jenkins

rm -rf /var/cache/jenkins
rm -rf /var/lib/jenkins/
rm -rf /var/log/jenkins

```