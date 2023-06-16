systemctl status nginx
systemctl restart nginx

systemctl restart mysqld

---  -----
git status  查看当前仓库状态
git add .   将自己修改的文件 添加到git 暂存区
git commit -m 'up somethine'  暂存区内容提交到当前分支
git push   将当前分支 推送到 远程仓库
git pull   拉取当前远程仓库文件

git branch  //查看分支
git branch dev  //创建分支
git merge dev //将dev 分支合并到当前分支上

git checkout daigou
git switch master
git switch daigou
git switch zxl
git merge daigou

git branch  //查看分支
git merge dev //将dev 分支合并到当前分支上
git checkout -b dev //创建分支 并进入创建的分支
git checkout -b develop //创建分支 并进入创建的分支
git branch dev  //创建分支
git checkout dev  //切换分支
实际上，切换分支这个动作，用switch更科学
	git switch -c dev  创建并切换到新的dev分支
	git switch master  切换分支
	git branch -d feature1 


强制将远程代码git步到本地
	git fetch --all && git reset --hard origin/master
	git fetch --all && git reset --hard origin/hanguo_easybayfast
	git fetch --all && git reset --hard origin/daigou
	git fetch --all && git reset --hard origin/dev

命令直接把仓库提交地址改了
	git fetch --all && git reset --hard origin/wangzong
	git remote set-url origin 新仓库地址

# git忽略不提交的文件3种情形
1、从未提交过的文件可以用.gitignore 也就是添加之后从来没有提交（commit）过的文件，可以使用.gitignore忽略该文件 该文件只能作用于未跟踪的文件（Untracked Files），也就是那些从来没有被 git 记录过的文件
比如，忽略log/下的日志文件。可以在.gitignore中写

log/*

想忽略一个目录下的所有文件(包括文件夹),但要保留这个文件夹方法

方法1、空目录empty中添加 .gitignore 文件，内容是

# 忽略所有文件
*
# 除了这个文件
!.gitignore
然后 git add empty 即可。

方法2、就是在目录下新建一个 .gitkeep 文件（文件名其实随意，不过常见的是 .gitkeep 和 .keep）

2、已经推送（push）过的文件，想从git远程库中删除，并在以后的提交中忽略，但是却还想在本地保留这个文件.
先用方法1 在 .gitignore添加需要忽略的文件 再执行命令

git rm --cached Xml/config.xml

#注意：如果出现下列错误可以用以下方式解决问题
# fatal: not removing 'tencent' recursively without -r
#解决：用git rm --cached来删除文件夹的追踪状态是出现
git rm -r --cached tencent
后面的 Xml/config.xml 是要从远程库中删除的文件的路径，支持通配符* 比如，不小心提交到git上的一些log日志文件，想从远程库删除，可以用这个命令

3、已经推送（push）过的文件，想在以后的提交时忽略此文件，即使本地已经修改过，而且不删除git远程库中相应文件.
执行命令

git update-index --assume-unchanged Xml/config.xml 

git update-index –no-assume-unchanged –path 可以取消忽略文件 
#后面的 Xml/config.xml 是要忽略的文件的路径
如果要忽略一个目录，打开 git bash，cd到 目标目录下，执行：

git update-index --assume-unchanged $(git ls-files | tr '\n' ' ')

比如有一个配置文件记录数据库的链接信息，每个人的链接信息肯定不一样，但是又要提供一个标准的模板，用来告知如何填写链接信息，那么就需要在git远程库上有一个标准配置文件，然后每个人根据自己的具体情况，修改一份链接信息自用，而且不会将该配置文件提交到库。


查找 包含字符串文件
find  /etc/httpd/conf.d/  -name  "*.conf"   -type f  |  xargs  grep     "important"
find  /etc/nginx/conf.d/  -name  "*.conf"   -type f  |  xargs  grep     "cliqsrc_com.pem"
fdisk -l 磁盘列表
挂载磁盘
mount  /dev 目录


在 CentOS7 中，使用 systemd 来管理其他服务是否开机启动，systemctl 是 systemd 服务的命令行工具

[root@mysql ~]# systemctl start httpd.service //启动服务

[root@mysql ~]# systemctl stop httpd.service //关闭服务

[root@mysql ~]# systemctl restart httpd.service //重启服务

[root@mysql ~]# systemctl status httpd.service //查看服务状态

[root@mysql ~]# systemctl is-enabled httpd.service //查看指定的服务是否开机启动

[root@mysql ~]# systemctl enable httpd.service //设置指定的服务开机启动

[root@mysql ~]# systemctl disable httpd.service //设置指定的服务开机不启动



[{"name":"business","placeholder":"webmoney账号"},
{"name":"webmoney_currency_code","placeholder":"webmoeny货币"},
{"name":"webmoney_currency_code_rate","placeholder":"webmoney收款货币对应主货币汇率"},{"name":"paypal_currency_decaimal","placeholder":"webmoney收款货币四舍五入保留小数"},
{"name":"pay_fee","placeholder":"支付手续费"}
]






