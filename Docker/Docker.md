### 常用命令
```
# 状态
sudo service docker status

# 启动
sudo systemctl start docker

# 停止一个docket服务
sudo docker stop gitlab

# 删除一个dockers服务
sudo docker rm gitlab
```
Docker版本
```
sudo docker --version
```
查看正在运行的容器
```
sudo docker ps
```
查看所有的容器
```
sudo docker ps -a
```
查看本地镜像
```
sudo docker images
```
搜索Docker Image
```
docker search tutorial
```
通过docker命令下载镜像
```
docker pull 
```

查看某个container的运行日志
```
docker logs [container]

# 类似tailf
docker logs -f [container] 
```

从镜像中运行/停止一个新实例
```
sudo docker run/stop --help
sudo docker run/stop container
```










把当前用户加入到docker组就可以直接使用命令，而不用每次都加sudo
```
sudo groupadd docker
```
改完后需要重新登陆用户
```
sudo gpasswd -a ${USER} docker
```