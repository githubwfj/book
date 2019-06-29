#### Docker支持以下的CentOS版本：
- CentOS 7 (64-bit)
- CentOS 6.5 (64-bit) 或更高的版本

### 前提条件
- 目前，CentOS 仅发行版本中的内核支持 Docker。
- Docker 运行在 CentOS 7 上，要求系统为64位、系统内核版本为 3.10 以上。
- Docker 运行在 CentOS-6.5 或更高的版本的 CentOS 上，要求系统为64位、系统内核版本为 2.6.32-431 或者更高版本。

### 使用 yum 安装（CentOS 7下）
Docker 要求 CentOS 系统的内核版本高于 3.10 ，查看本页面的前提条件来验证你的CentOS 版本是否支持 Docker 。
```
# 查看系统当前的内核版本
uname -r 
```

### 安装 Docker
从 2017 年 3 月开始 docker 在原来的基础上分为两个分支版本: Docker CE 和 Docker EE。

Docker CE 即社区免费版，Docker EE 即企业版，强调安全，但需付费使用。

移除旧的版本：
```
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine
```
安装一些必要的系统工具：
```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```
添加软件源信息：
```
sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```
更新 yum 缓存：
```
sudo yum makecache fast
```
安装 Docker-ce
```
sudo yum -y install docker-ce
```
启动 Docker 后台服务
```
sudo systemctl start docker
```
测试运行 hello-world
```
docker run hello-world
```
由于本地没有hello-world这个镜像，所以会下载一个hello-world的镜像，并在容器内运行。

### 删除 Docker CE
```
sudo yum remove docker-ce
sudo rm -rf /var/lib/docker
```


### 使用脚本安装 Docker
1、使用 sudo 或 root 权限登录 Centos。
2、确保 yum 包更新到最新。
```
sudo yum update
```
执行 Docker 安装脚本
```
curl -fsSL https://get.docker.com -o get-docker.sh

sudo sh get-docker.sh
```
执行这个脚本会添加 docker.repo 源并安装 Docker。

启动 Docker 进程。
```
sudo systemctl start docker
```