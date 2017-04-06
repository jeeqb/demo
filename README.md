# demo
6、安装GitLab

将GitLab安装在git的家目录下：

$ su -
$ su - git
a、克隆GitLab并切换分支到6-3-stable

# 克隆GitLab
$ git clone https://github.com/gitlabhq/gitlabhq.git gitlab
# 进入gitlab目录
$ cd /home/git/gitlab
# 切换到6-3-stable分支
$ git checkout 6-3-stable
b、配置项目

# 复制配置文件
$ cp config/gitlab.yml.example config/gitlab.yml

# 修改配置文件中的访问域名
（your_domain_name为项目的访问域名）
$ sed -i 's|localhost|your_domain_name|g' config/gitlab.yml

# 设定log和tmp目录所有者和权限
$ chown -R git log/
$ chown -R git tmp/
$ chmod -R u+rwX log/
$ chmod -R u+rwX tmp/

# 创建gitlab-satellites目录
$ mkdir /home/git/gitlab-satellites

# 创建tmp/pids/和tmp/sockets/目录，确保gitlab有相应的权限
$ mkdir tmp/pids/
$ mkdir tmp/sockets/
$ chmod -R u+rwX tmp/pids/
$ chmod -R u+rwX tmp/sockets/
