
## 命令
``` gitlab
# 重新配置应用程序,相当于初始化一下
gitlab-ctl reconfigure

# 重启gitlab
gitlab-ctl restart

# 关闭gitlab 
gitlab-ctl stop

# 启动gitlab
gitlab-ctl start

# gitlab状态
gitlab-ctl status

# 禁止 Gitlab 开机自启动：
systemctl disable gitlab-runsvdir.service

# 启用 Gitlab 开机自启动：
systemctl enable gitlab-runsvdir.service

# 查看版本 
cat /opt/gitlab/embedded/service/gitlab-rails/VERSION

netstat -nultp |grep :80
```
### 修改域名
```
vim /etc/gitlab/gitlab.rb

external_url 'http://ip'

external_url 'http://'

```

### 默认gitlab仓库存储位置
```
cd /var/opt/gitlab/git-data/repositories
```
### 修改gitlab仓库存储位置
```
vim /etc/gitlab/gitlab.rb

# 启用 git_data_dirs 参数，修改格式:
git_data_dirs({
    "default" => {
    "path" => "/data/git-data",
    "failure_count_threshold" => 10,
    "failure_wait_time" => 30,
    "failure_reset_time" => 1800,
    "failure_timeout" => 30
    }
})
```