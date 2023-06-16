由于以前的url直接防止账号密码存在安全隐患，已经导致zzqss git账号密码泄露代码被删改特改用新的配置方法。

1、  检查服务器是否存在ssh密钥

查看目录

/root/.ssh

是否存在文件 id_rsa id_rsa.pub

如果存在跳过第二步

2、  创建新的ssh密钥公钥

```
ssh-keygen -t rsa -C "国家缩写+ip最后一段@zzqss.com"例如：ssh-keygen -t rsa -C "cn126@zzqss.com"
```

3、  添加部署密钥![](https://docimg10.docs.qq.com/image/AgAABf7UeHbUpVPuuxdBpbCxw6PDMRAT.png?w=1252&h=729)

内容为上一步生成的 id_rsa.pub 文件内容。

4、  修改远程仓库地址

```
.git/config 仓库地址修改为ssh仓库例如：ssh://git@git.zzqss.cn:222/lpj/equipment_manager.git
```

5、  检查webhook的同步代码![](https://docimg8.docs.qq.com/image/AgAABf7UeHa0O7Yt2alEkoApSCJ_ho4x.png?w=1249&h=695)

修改为ssh地址

6、  完成，可以测试git pull 拉去代码