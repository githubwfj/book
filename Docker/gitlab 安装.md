#### 1.克隆gitlab-ce
```
sudo docker pull gitlab/gitlab-ce:latest
```
#### 2.创建docker container
注意，这里因为作者的服务器80端口等已经被占用，所以，对端口进行了映射
```
sudo docker run -d -p 8443:443 -p 8081:80 -p 8022:22 \
--name gitlab --restart always \
--volume /home/dockerData/gitlab/config:/etc/gitlab \
--volume /home/dockerData/gitlab/logs:/var/log/gitlab \
--volume /home/dockerData/gitlab/data:/var/opt/gitlab \
gitlab/gitlab-ce:latest
```
'/home/dockerData/gitlab'是映射到物理机上的卷的路径。可以根据需要自定义。 

另外，注意映射端口时，避免使用8080端口，因为8080在docker内部被Unicorn占用


#### 3.访问并测试 
首次启动比较慢，所以，需要稍等一会儿，就可以在对应http://ip:8081 链接中访问到页面。初次使用时，需要我们创建默认的管理员密码。当登录之后，创建项目，突然发现，坏了。 
在项目clone的路径中，本来应该是:8081的地方，变成了主机名。

#### 4.修改配置 
为了解决这个问题，我们需要修改external_url，
```
sudo docker exec -it gitlab /bin/bash
vim /etc/gitlab/gitlab.rb

# 修改external_url为
external_url "http://ip:8081"

# 运行gitlab-ctl使配置生效
gitlab-ctl reconfigure

# 重启
gitlab-ctl restart
```

#### 5.再次测试 
再次访问http://ip:8081，发现，访问不了了。。 

修改external_url时，container内部的项目端口竟然也被直接转到了8081端口上，而原来我们映射的端口时8081:80，此时，80端口上没东西了，造成访问不了了。所以，删掉这个容器，重新创建
```
# 停止
sudo docker stop gitlab
# 删除
sudo docker rm gitlab
# 启动
sudo docker run -d -p 8443:443 -p 8081:8081 -p 8022:22 \
--name gitlab --restart always \
--volume /home/dockerData/gitlab/config:/etc/gitlab \
--volume /home/dockerData/gitlab/logs:/var/log/gitlab \
--volume /home/dockerData/gitlab/data:/var/opt/gitlab \
gitlab/gitlab-ce:latest
```