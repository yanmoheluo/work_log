进入到当前目录执行命令，先上图后分解

![](https://img-blog.csdnimg.cn/20200301145016781.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzMzE2Nzg0,size_16,color_FFFFFF,t_70)

获取SSH或者HTTPS地址

![](https://img-blog.csdnimg.cn/947600957bcf40dfbaa2697373f16767.png)

[git命令](https://so.csdn.net/so/search?q=git%E5%91%BD%E4%BB%A4&spm=1001.2101.3001.7020)模式进入当前项目目录查看当前：

$ git remote -v

SSH切换HTTP:

git remote set-url origin https://github.com/luojunchong/PLAN.git

HTTP切换SSH:

$ git remote set-url origin git@github.com:luojunchong/PLAN.git

到此演示完毕！



git remote set-url origin ssh://git@git.zzqss.cn:222/zxl/ceshi2.git