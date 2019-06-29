### 1.安装并配置必要的依赖项
在CentOS 7（和RedHat / Oracle / Scientific Linux 7）上，以下命令还将在系统防火墙中打开HTTP和SSH访问。
```
sudo yum install -y curl policycoreutils-python openssh-server openssh-clients
sudo systemctl enable sshd
sudo systemctl start sshd
sudo firewall-cmd --permanent --add-service=http
sudo systemctl reload firewalld
```
接下来，安装Postfix以发送通知电子邮件。如果要使用其他解决方案发送电子邮件，请跳过此步骤并在安装GitLab后[配置外部SMTP服务器](https://docs.gitlab.com/omnibus/settings/smtp.html)。
```
sudo yum install postfix
sudo systemctl enable postfix
sudo systemctl start postfix
```
在Postfix安装期间，可能会出现配置屏幕。选择“Internet Site”并按Enter键。使用服务器的外部DNS作为“邮件名称”，然后按Enter键。如果出现其他屏幕，请继续按Enter键接受默认值。

### 2.添加GitLab软件包存储库并安装软件包
添加GitLab包存储库。
```
# 企业版
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.rpm.sh | sudo bash
# 社区版
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | sudo bash

```
接下来，安装GitLab包。更改https://gitlab.example.com为您要访问GitLab实例的URL。安装将自动配置并启动该URL的GitLab。

对于https://URL，GitLab将自动[使用Let's Encrypt请求证书，该证书](https://docs.gitlab.com/omnibus/settings/ssl.html#lets-encrypthttpsletsencryptorg-integration)需要入站HTTP访问和有效的主机名。您也可以[使用自己的证书](https://docs.gitlab.com/omnibus/settings/nginx.html#manually-configuring-https)或只使用http://。
```
# 企业版
yum install -y gitlab-ee

# 社区版
yum install -y gitlab-ce
```
### 3.浏览到主机名并登录
在您第一次访问时，您将被重定向到密码重置屏幕。提供初始管理员帐户的密码，您将被重定向回登录屏幕。使用默认帐户的用户名root登录。

有关[安装和配置的详细说明](https://docs.gitlab.com/omnibus/README.html#installation-and-configuration-using-omnibus-package)，请参阅我们的[文档](https://docs.gitlab.com/omnibus/README.html#installation-and-configuration-using-omnibus-package)。

### 4.设置通信首选项
访问我们的[电子邮件订阅偏好中心](https://about.gitlab.com/company/preference-center/)，告知我们何时与您沟通。我们有明确的电子邮件选择加入政策，因此您可以完全控制我们向您发送电子邮件的频率和频率。

每月两次，我们会发送您需要了解的GitLab新闻，包括我们开发团队的新功能，集成，文档和幕后故事。有关错误和系统性能的重要安全更新，请注册我们的专用安全通讯。

重要说明：如果您不选择加入安全通讯，则不会收到安全警报。

