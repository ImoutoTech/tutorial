之前的教程中，我们把VPS类比成毛胚房，要想让我们的博客“住”进去，还得家具，装修。而家具就是运行环境了。我们首先来搞明白，我们要安装什么，以及为什么要安装它们。

从第一节课中我们知道，博客系统的运行是基于一定的语言环境的，所以我们需要安装网站的**语言环境**，例如`PHP`。而大多数博客的数据是储存在数据库中的，意味着我们需要安装**数据库**软件，例如`MYSQL`。那么到现在博客的运行是没有问题了，但是想要让人们能访问它，我们还得安装一个**WEB服务器**，例如Nginx。这就是一般个人网站环境的“三大件”。

然而，我们一个个手动安装的话，不仅耗时费心，还容易踩坑出错。好在有免费的外包公司，免去了我们的麻烦。而今天的主角就是外包公司的其中之一——宝塔面板。

### 安装宝塔

宝塔的安装十分方便。首先用SSH连接上你的服务器，在[宝塔安装说明](https://bt.cn/bbs/thread-19376-1-1.html)处找到你对应的系统，获得安装指令，复制到你的服务器执行即可。

![获取安装指令](https://cdn.exia.xyz/img/imouto/course5/bt_install.jpg)

例如我的服务器系统为debian9，那么将debian对应的命令复制去服务器执行，不过记得先新建一个窗口先，避免中途掉线。

```bash
screen -S bt
wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh && bash install.sh
```

![天才第一步](https://cdn.exia.xyz/img/imouto/course5/install1.jpg)

按下回车，剩下来的就等他自己慢慢运行了。安装的速度是根据服务器性能决定的，通常不会太久。一般等个个把分钟就好了。安装完成后会得到面板信息

```bash
Bt-Panel: http://服务器IP:8888/079cd700
username: k4fdgams
password: 4f0708cc
If you cannot access the panel,
release the following panel port [8888] in the security group
若无法访问面板，请检查防火墙/安全组是否有放行面板[8888]端口
```

接下来按照所给的地址与用户名密码登录面板即可。

![天才第二步](https://cdn.exia.xyz/img/imouto/course5/install2.jpg)

第一次登录时会建议你安装一些套件，这里有两个选择无非是WEB服务器的区别。而至于两者的区别，不用过于探究，毕竟在我们这个访问量来说是没什么去别的。哪个顺眼就使哪个吧。如果要细究两者的区别的话，可以看看这个[提问](https://www.zhihu.com/question/19571087/answer/12313829)。

之后呢，宝塔就会自动帮我们安装辣，我们可以通过面板左上角的通知气泡来查看安装情况。

![天才第三步](https://cdn.exia.xyz/img/imouto/course5/install4.jpg)

当任务列表提示“无任务”之后，就安装完啦。

![搞定](https://cdn.exia.xyz/img/imouto/course5/install5.jpg)



至此，网站环境的安装就大功告成，下一节就开始配置网站！