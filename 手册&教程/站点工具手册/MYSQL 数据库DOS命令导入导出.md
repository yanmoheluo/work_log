**MySQL命令行导出数据库**

1，进入MySQL目录下的bin文件夹：cd MySQL中到bin文件夹的目录

如我输入的命令行：cd C:\Program Files\MySQL\MySQL Server 4.1\bin

(或者直接将windows的环境变量path中添加该目录)

2，导出数据库：mysqldump -u 用户名 -p 数据库名 > 导出的文件名

如我输入的命令行:mysqldump -u root -p news > news.sql   (输入后会让你输入进入MySQL的密码)

（如果导出单张表的话在数据库名后面输入表名即可）

3、会看到文件news.sql自动生成到bin文件下 

**命令行导入数据库**

1，将要导入的.sql文件移至bin文件下，这样的路径比较方便  
2，同上面导出的第1步  
3，进入MySQL：mysql -u 用户名 -p

如我输入的命令行:mysql -u root -p   (输入同样后会让你输入MySQL的密码)

4，在MySQL-Front中新建你要建的数据库，这时是空数据库，如新建一个名为news的目标数据库  
5，输入：mysql>use 目标数据库名

如我输入的命令行:mysql>use news;

6，导入文件：mysql>source 导入的文件名;

如我输入的命令行：mysql>source news.sql;

MySQL备份和还原,都是利用mysqldump、mysql和source命令来完成的。

**备份数据库：**进入cmd  
导出所有数据库：输入：mysqldump -u [数据库用户名] -p -A>[备份文件的保存路径]  
  
导出数据和数据结构：输入：mysqldump -u [数据库用户名] -p [要备份的数据库名称]>[备份文件的保存路径]  
例子：mysqldump -u root -p test>d:\test.sql  
注意：此备份只备份数据和数据结构，没有备份存储过程和触发器  
  
只导出数据不导出数据结构：输入：mysqldump -u [数据库用户名] -p -t [要备份的数据库名称]>[备份文件的保存路径]  
  
**导出数据库中的Events**输入：mysqldump -u [数据库用户名] -p -E [数据库用户名]>[备份文件的保存路径]  
  
**导出数据库中的存储过程和函数**mysqldump -u [数据库用户名] -p -R [数据库用户名]>[备份文件的保存路径]  
  
**导入数据库**   
mysql -u root -p<[备份文件的保存路径] 疑问  
  
**恢复备份文件：**进入MYSQL Command Line Client  
先创建数据库：create database test 注：test是创建数据库的名称  
再切换到当前数据库：use test  
再输入：\. d:/test.sql 或 souce d:/test.sql  
  
**1. 概述****MySQL数据库的导入，有两种方法：**1) 先导出数据库SQL脚本，再导入；  
2) 直接拷贝数据库目录和文件。  
  
在不同操作系统或MySQL版本情况下，直接拷贝文件的方法可能会有不兼容的情况发生。  
所以一般推荐用SQL脚本形式导入。下面分别介绍两种方法。  
  
**2. 方法一 SQL脚本形式**操作步骤如下：  
2.1. 导出SQL脚本  
在原数据库服务器上，可以用phpMyAdmin工具，或者mysqldump(mysqldump命令位于mysql/bin/目录中)命令行，导出SQL脚本。  
2.1.1 用phpMyAdmin工具  
导出选项中，选择导出“结构”和“数据”，不要添加“Drop DATABASE”和“Drop TABLE”选项。  
选中“另存为文件”选项，如果数据比较多，可以选中“gzipped”选项。  
将导出的SQL文件保存下来。  
  
2.1.2 用mysqldump命令行  
命令格式  
mysqldump -u用户名 -p 数据库名 > 数据库名.sql  
范例：  
mysqldump -uroot -p abc > abc.sql  
（导出数据库abc到abc.sql文件）  
  
提示输入密码时，输入该数据库用户名的密码。  
  
2.2. 创建空的数据库  
通过主控界面/控制面板，创建一个数据库。假设数据库名为abc，数据库全权用户为abc_f。  
  
2.3. 将SQL脚本导入执行  
同样是两种方法，一种用phpMyAdmin（mysql数据库管理）工具，或者mysql命令行。  
2.3.1 用phpMyAdmin工具  
从控制面板，选择创建的空数据库，点“管理”，进入管理工具页面。  
在"SQL"菜单中，浏览选择刚才导出的SQL文件，点击“执行”以上载并执行。  
  
注意：phpMyAdmin对上载的文件大小有限制，php本身对上载文件大小也有限制，如果原始sql文件  
比较大，可以先用gzip对它进行压缩，对于sql文件这样的文本文件，可获得1:5或更高的压缩率。  
gzip使用方法：  
# gzip xxxxx.sql  
得到  
xxxxx.sql.gz文件。  
  
2.3.2 用mysql命令行  
命令格式  
mysql -u用户名 -p 数据库名 < 数据库名.sql  
范例：  
mysql -uabc_f -p abc < abc.sql  
（导入数据库abc从abc.sql文件）  
  
提示输入密码时，输入该数据库用户名的密码。  
  
3 方法二 直接拷贝  
如果数据库比较大，可以考虑用直接拷贝的方法，但不同版本和操作系统之间可能不兼容，要慎用。  
3.1 准备原始文件  
用tar打包为一个文件  
  
3.2 创建空数据库  
  
3.3 解压  
在临时目录中解压，如：  
cd /tmp  
tar zxf mydb.tar.gz  
  
3.4 拷贝  
将解压后的数据库文件拷贝到相关目录  
cd mydb/  
cp * /var/lib/mysql/mydb/  
  
对于FreeBSD:  
cp * /var/db/mysql/mydb/  
  
3.5 权限设置  
将拷贝过去的文件的属主改为mysql:mysql，权限改为660  
chown mysql:mysql /var/lib/mysql/mydb/*  
chmod 660 /var/lib/mysql/mydb/*