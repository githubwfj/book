### 使用Apache2.x 搭建文件服务器

#### yum 安装
```
# apache服务的软件包名称叫做httpd
yum install httpd -y
```
#### apt 安装
```
apt-getinstall apache2
```

#### 启动
```
# 启动
systemctl start httpd

# 开机启动
systemctl enable httpd

# 重启
systemctl restart httpd

```

##### 配置文件
服务目录	 | /etc/httpd
---|---
主配置文件	 | /etc/httpd/conf/httpd.conf
网站数据目录 | /var/www/html
网站数据目录 | /var/www/html
访问日志	 | /var/log/httpd/access_log
错误日志	 | /var/log/httpd/error_log

##### 在httpd服务程序主配置文件中最为常用的参数包括有：
ServerRoot   | 服务目录
---|---
ServerAdmin  | 管理员邮箱
User	     | 运行服务的用户
Group	     | 运行服务的用户组
ServerName	 | 网站服务器的域名
DocumentRoot | 网站数据目录
Listen	     | 监听的IP地址与端口号
DirectoryIndex	| 默认的索引页页面
ErrorLog	 | 错误日志文件
CustomLog	 | 访问日志文件
Timeout	     | 网页超时时间,默认为300秒.
Include	     | 需要加载的其他文件

