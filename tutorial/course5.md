[Oneinstack](https://oneinstack.com/)是一种懒人式的web环境一键安装脚本，与此类似的呢还有[lnmp](https://lnmp.org/)，[lamp](https://lamp.sh/)等。那么它们与宝塔这类面板的区别主要就在于这类一键安装包没有WEB的后台界面，主要是靠我们直接通过命令行来操作。不过它们也因此更加的轻量，便捷。

那么我们如何安装及使用呢？

### 安装

首先我们来到oneinstack的官网 https://oneinstack.com 。在上方的导航栏中我们选中自动安装。

![auto](https://cdn.exia.xyz/img/imouto/course6/oneinstack1.png)

这里可能大家会看得有点眼花缭乱了。但是我们不用担心，直接复制安装指令即可。如果你想再详细了解一下可以看一下下面的说明。

我们之前提到过，WEB环境主要由WEB服务器，语言环境和数据库组成，对应图中的`nginx`，`PHP`，`数据库`。也就是说这三个我们是必须安装的，而PHP这里呢又有个`PHP拓展`的选项。这个主要是通过给PHP安装一些拓展来使它能够实现更多功能，例如`imagick`可以让PHP进行图片编辑的操作。一般来说呢，我们搭建博客是不需要什么PHP拓展的，所以我们基本上不用关这些配置什么的。对于需要几个PHP这个问题呢，对于一般用户来说一个PHP环境足矣，版本呢建议就在7.2以上吧。

数据库这边，因为博主涉猎不深，对此没有太大的理解，所以就不发表意见了。不过一般来说安装`mysql`是适用性最广的，可以放心安装。

再看到下面的一小排选择框，这里呢需要给大家一一解释一下。

> #### Pure-FTPd
>
> 这个用于搭建FTP服务器，让用户可以通过FTP协议链接服务器进行文件管理。其多用户系统可以非常好的划分每一位用户可浏览的目录，不会相互干扰。
>
> 使用场景：多人共用一台服务器时可以使用，例如虚拟主机。
>
> #### phpMyAdmin
>
> 神器级别的数据库管理系统。由于数据库一般是通过代码行直接操作，需要学习~~大量的~~一些指令，而phpMyAdmin简化了这一过程，为我们提供了可视化的界面，从此数据库不再是烦恼。
>
> 使用场景：都可
>
> #### redis
>
> Redis 是一个高性能的key-value数据库，博客基本用不上，不过可能会有一些插件支持，所以还是可以勾上的。
>
> #### memcached
>
> memcached是一套分布式的快取系统，与redis相似。
>
> #### HHVM
>
> 基本没啥用。
>
> #### iptables
>
> “防火墙”，更多解释可以看一下[朱双印](http://www.zsythink.net/archives/1199)大佬的博文。



到这里就基本解释完了。**总结**，一般的博主们不需要配置什么东西，直接到下面复制安装指令即可。

那么现在去安装吧。

打开XSHELL，连接服务器。将复制好的安装指令粘上去执行，铁汁们，我这么做对吗？虽然没错，但是是不是少了点什么？对了！我们之前讲到过，为了防止各种突发情况，我们需要Screen来保证安装过程顺利进行。

```shell
#首先
screen -S oneinstack

#执行安装指令
wget -c http://mirrors.linuxeye.com/oneinstack-full.tar.gz && tar xzf oneinstack-full.tar.gz && ./oneinstack/install.sh --nginx_option 1 --php_option 7 --phpcache_option 1 --phpmyadmin  --db_option 2 --dbinstallmethod 1 --dbrootpwd oneinstack --pureftpd  --redis  --memcached  --reboot 
```

接下来呢就可以关闭XSHELL，边喝茶边看书慢慢等即可。

过了一段时间之后，我们重新连接服务器。我们可以使用`screen -r oneinstack`指令重新连接回去。如果这个时候还在满屏刷一些不知道什么的鬼东西，而且还刷个不停，就是还在安装，再多等会就好。安装时间与服务器性能是挂钩的，机器越好，装得越快。

有过了一段时间再次连接回去，使用`screen -r oneinstack`时，却提示`There is no screen to be resumed matching oneinstack.`

![why?](https://cdn.exia.xyz/img/imouto/course6/oneinstack3.png)

那么恭喜，终于安装完啦！这个时候去浏览器，直接访问你服务器的ip地址试试看。

![yes](https://cdn.exia.xyz/img/imouto/course6/oneinstack4.png)

这里时oneinstack的引导页面，通过侧边栏的这些教学，你可以学习一下如何添加网站，如何自动备份等。那么，网站环境的安装到这里就结束啦！下节课开始就是网站的新建与安装咯。









