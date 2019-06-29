# Jenkins Debian packages

这是Jenkins的Debian软件包存储库，用于自动安装和升级。要使用此存储库，请先将密钥添加到系统中：

```
wget -q -O  - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add  -
```
然后在/etc/apt/sources.list中添加以下条目：
```
deb https://pkg.jenkins.io/debian-stable binary/
```
更新本地包索引，然后最终安装Jenkins：
```
sudo apt-get update 
sudo apt-get install jenkins
```

### 个人包下载[地址](https://pkg.jenkins.io/debian-stable/)
