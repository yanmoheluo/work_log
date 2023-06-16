一、绪论

ipfs全称InterPlanetary File System，即“星际文件系统”。顾名思义，文件系统，就是对文件进行管理的系统，比如电脑的NTFS、ext4、FAT32，以及苹果电脑的apfs，都是文件系统，而ipfs也是文件系统的一种形式，不过它是一种网络文件系统。前面我使用的[http://globalupload.io](http://globalupload.io/)也属于使用ipfs技术的网站。

![](https://pic3.zhimg.com/v2-be7ea10559515d166a7cc50d7648f436_r.jpg)

  

这是来自官网的截图，介绍了ipfs网络相较于传统网络的四大优势——高效（廉价）、持久、去中心化、开放。ipfs的本质，就是一个去中心化的文件分享系统。

实际上ipfs可以用作相当多的用途，比如托管去中心化论坛、托管网站等。但本教程不讨论这些进阶内容，仅介绍如何使用ipfs简单地托管并分享文件。

二、使用教程

ipfs的图形化客户端可以在[https://github.com/ipfs-shipyard/ipfs-desktop/releases/](https://github.com/ipfs-shipyard/ipfs-desktop/releases/) 下载。Github文件可使用[https://g.ioiox.com/](https://g.ioiox.com/) 进行加速，只需复制下载链接进去即可。

具体步骤为：

![](https://pic1.zhimg.com/v2-0f26eaf5a29b1e45ae6f621256898868_r.jpg)

首先打开上面的github链接，然后往下滚。

![](https://pic1.zhimg.com/v2-b04a18acbef5967c26c0bdfa9bef7558_r.jpg)

找到后缀是.exe的文件，右键，选择“复制链接地址”。

![](https://pic3.zhimg.com/v2-1c2697741c44a3d8653bc633edd5456e_r.jpg)

然后去[https://g.ioiox.com](https://g.ioiox.com/) 输入框里粘贴链接，点下载。

在这里，Windows用户需要下载的是扩展名为.exe的文件。本教程下载的安装文件名为“IPFS-Desktop-Setup-0.12.2.exe”。

![](https://pic1.zhimg.com/80/v2-878b5ed88d124862111e544791404d74_1440w.webp)

安装过程不再赘述，可以选择是给自己这个用户安装还是给整台电脑安装，如果你的电脑只有你一个用户，那么两者的区别不大。（本质是C:\Users\用户名\Appdata和C:\Program Files 的区别）

![](https://pic1.zhimg.com/80/v2-40458857e42acfb549ea67c9839c4e94_1440w.webp)

安装好后右键托盘图标打开菜单，ipfs默认开机不会自启动，可在配置-Launch at Login开启。

先讲一下如何上传文件：

我们在右键菜单中选择“文件”。然后我们进入了这个界面：

![](https://pic1.zhimg.com/v2-e4b7a0681ce8d18f0452f7babe29cd60_r.jpg)

然后点导入-文件（夹），选择需要上传的文件，确认即可。

我们这里拿红雅的法西斯科普PDF来作例子：

![](https://pic2.zhimg.com/v2-72d25d65b7ff6e4dd7aa76cf220cdd59_r.jpg)

接下来是如何分享文件：

右键文件，选择“复制CID”（注意不是“分享链接”），CID大概长这样：

QmUoqPMfF2zekW5GiDCsBsVaa794n8u118dtLU7quUVeSn

然后，我们把CID加在[https://ipfs.globalupload.io/](https://ipfs.globalupload.io/) 后面，比如这个PDF的下载链接就会是这样：

[https://ipfs.globalupload.io/QmUoqPMfF2zekW5GiDCsBsVaa794n8u118dtLU7quUVeSn](https://ipfs.globalupload.io/QmUoqPMfF2zekW5GiDCsBsVaa794n8u118dtLU7quUVeSn)

好了，你可以把这个链接丢出去给别人用了。值得一提的是，以这样的方法可以绕开globalupload上传大小25MB的限制。注意在整完了之后别在这个界面右键文件选“删除”，因为这相当于向整个ipfs网络广播删除这个文件，结果是不可逆的。不过，电脑上的原文件可以删除了，这对分享的文件不会产生太大的影响。

三、进阶使用——加速下载

其实ipfs有个官网，把CID加在[https://ipfs.io/ipfs/](https://ipfs.io/ipfs/) 后同样可以实现下载链接的效果。然而，[http://ipfs.io](http://ipfs.io/)处于被墙状态，这使得我们不得不使用其它的Gateway。

什么是Gateway呢？我们可以这样理解：ipfs网络是与我们熟知的网络相隔离的网络体系，而Gateway正是这二者之间的桥梁。通过任意gateway均可实现对ipfs的访问。而前文提到的[http://ipfs.globalupload.io](http://ipfs.globalupload.io/)正是一个gateway。

除了通过gateway访问文件，我们还可以直接使用ipfs本身来访问文件。例如，前文分享的红雅法西斯PDF，我们拿到了这一串CID：

QmUoqPMfF2zekW5GiDCsBsVaa794n8u118dtLU7quUVeSn

在ipfs客户端右键菜单里，选择“文件”，然后选择导入-来自ipfs路径，输入这串CID，并点击“导入”

![](https://pic2.zhimg.com/v2-96ea541b579c842598fd05ad55572839_r.jpg)

结果是这样的：

![](https://pic2.zhimg.com/v2-c8708f8b61b448bfa0a1b8e48bb833ad_r.jpg)

这样有个缺点，就是会丢失文件名，包括扩展名在内。

我们点那三个点，选择“下载”，保存下来之后，还得自己加上.pdf的扩展名才能正常打开。通过gateway则一般无此问题。

然而，好处在于，速度比使用gateway快很多，有时能达到满带宽。

最后再献上一篇通识手册作为P民的阅读津贴（迫真）：

QmTmdcq1apbqC5YL5j7Jum2dqd5DCsyYs1NMoGNG5rj3jU