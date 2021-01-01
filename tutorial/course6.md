前面我们已经搭建好了网站运行环境，那么现在我们就可以新建我们的网站啦。

### 域名解析

这里以阿里云的DNS控制面板来做个示范，来到解析控制台，点击按钮增加解析。

![新增解析](https://cdn.exia.xyz/img/imouto/course7/3.png)

![具体参数](https://cdn.exia.xyz/img/imouto/course7/4.png)

这里的各项都给个解释吧。

> **记录类型**
>
> 常见的有两种类型，分别是`A`，`CNAME`。
>
> `A`记录是直接解析到IP的，一般我们自己用VPS建站的时候会用到
>
> `CNAME`记录是解析到另一个域名，一般我们使用虚拟主机或者其他托管服务时会遇到
>
> **主机记录**
>
> 就是指你的域名前缀，例如我这里填的`blog`，代表说我正在把`blog.hk416.space`解析到目标地址。如果我想解析`www.hk416.space`要怎么办呢？对啦，主机记录这里就填上`www`就好了。
>
> P.S 如果我们想直接解析整个根域名(`hk416.space`)，那么我们需要填写的主机记录值为`@`，我们称之为`泛解析`
>
> **解析路线**
>
> 暂时与我们没什么关系
>
> **记录值**
>
> 就是你要解析到的地方啦，这里我们填上我们的服务器IP即可。

都填写完成之后，我们点击确认来保存。接下来就可以去服务器那里新建网站了。



### Oneinstack命令行操作

在我们安装好oneinstack之后，进入Oneinstack的文件夹，输出一下文件夹下的内容，我们可以看到

![oneinstack目录内容](https://cdn.exia.xyz/img/imouto/course7/2.png)

> #### 知识拓展
>
> 这里不同的颜色高亮表示不同的文件类型或者文件夹。一般这些绿色的以`.sh`结尾的为可执行的脚本文件。蓝色的则表示文件夹，而没有高亮的惨白色的则为普通的文件。

我们添加网站需要用到的就是右下角被水印挡住的`vhost.sh`了。但是在这之前，为了能让我们搭建网站的过程中能够顺利申请到SSL证书，我们需要先将域名解析至我们的服务器。记得哦！

回到XSHELL，在**Oneinstack目录下**，运行`vhost.sh`来新建网站

```shell
#进入Oneinstack文件夹
cd /path/to/oneinstack
#运行脚本
./vhost.sh
```

这里我们可以看到他的一个欢迎界面，然后就会开始一系列的选择，这里我会把所有选项的含义与注意事项标注出来。

```shell
#######################################################################
#       OneinStack for CentOS/RedHat 6+ Debian 8+ and Ubuntu 14+      #
#       For more information please visit https://oneinstack.com      #
#######################################################################

What Are You Doing? 
	1. Use HTTP Only  #只使用http新建网站
	2. Use your own SSL Certificate and Key #新建网站，并使用自己的SSL证书与密钥
	3. Use Lets Encrypt to Create SSL Certificate and Key #新建网站，顺便帮我使用Lets Encrypt来创建一个免费的证书
	q. Exit #打扰了
Please input the correct option: 3
#这里建议选择3选项，除非你有更好的SSL证书选择

Please input domain(example: www.example.com): blog.hk416.space
#请输入你的域名，这里填写刚刚解析的域名，要加上前缀

domain=blog.hk416.space

Please input the directory for the domain:blog.hk416.space :
(Default directory: /data/wwwroot/blog.hk416.space): 
#请输入网站数据的根目录，这里我们直接回车就好了
Virtual Host Directory=/data/wwwroot/blog.hk416.space

Create Virtul Host directory......
set permissions of Virtual Host directory......

Do you want to add more domain name? [y/n]: n
#你想要为这个网站添加更多域名吗？

Do you want to redirect all HTTP requests to HTTPS? [y/n]: y
#你想让你的网站强制https🐎？

#填写完这里之后，脚本就会自动帮你申请SSL证书，如果我们一开始没有解析的话，这里就会失败噢
.....
[Mon Sep  7 17:45:22 CST 2020] Your cert is in  /root/.acme.sh/blog.hk416.space/blog.hk416.space.cer 
[Mon Sep  7 17:45:22 CST 2020] Your cert key is in  /root/.acme.sh/blog.hk416.space/blog.hk416.space.key 
[Mon Sep  7 17:45:22 CST 2020] The intermediate CA cert is in  /root/.acme.sh/blog.hk416.space/ca.cer 
[Mon Sep  7 17:45:22 CST 2020] And the full chain certs is there:  /root/.acme.sh/blog.hk416.space/fullchain.cer 
nginx: the configuration file /usr/local/nginx/conf/nginx.conf syntax is ok
nginx: configuration file /usr/local/nginx/conf/nginx.conf test is successful
#申请完成

Do you want to add hotlink protection? [y/n]:y 
#你需要热链保护吗？这个地方随意吧，不过多一个防护总不是坏事

Allow Rewrite rule? [y/n]: y
#允许网址重写吗？这里为了以后我们的博客网址能比较自由美观，可以开一下。但是不开也不会有什么问题。
wordpress,opencart,magento2,drupal,joomla,codeigniter,laravel
thinkphp,pathinfo,discuz,typecho,ecshop,nextcloud,zblog,whmcs rewrite was exist.
(Default rewrite: other): typecho
#选择y后会给你一些自带的选项。这里对我们比较有用的无非wordpress,zblog,typecho了，看自己要选择什么博客程序来填写吧，这里我选择typecho

Allow Nginx/Tengine/OpenResty access_log? [y/n]: y
#最后一个问题，你需要网站的访问记录吗？当然需要
You access log file=/data/wwwlogs/blog.hk416.space_nginx.log

nginx: the configuration file /usr/local/nginx/conf/nginx.conf syntax is ok
nginx: configuration file /usr/local/nginx/conf/nginx.conf test is successful
Reload Nginx......

#######################################################################
#       OneinStack for CentOS/RedHat 6+ Debian 8+ and Ubuntu 14+      #
#       For more information please visit https://oneinstack.com      #
#######################################################################
Your domain:                  blog.hk416.space
Virtualhost conf:             /usr/local/nginx/conf/vhost/blog.hk416.space.conf
Directory of:                 /data/wwwroot/blog.hk416.space
Rewrite rule:                 /usr/local/nginx/conf/rewrite/typecho.conf
Let's Encrypt SSL Certificate:/usr/local/nginx/conf/ssl/blog.hk416.space.crt
SSL Private Key:              /usr/local/nginx/conf/ssl/blog.hk416.space.key
```

到这里，你的网站就建立好啦。去访问试试看吧。

![好耶！](https://cdn.exia.xyz/img/imouto/course7/5.png)

可以访问了！不过因为网站的根目录还没有文件。所以会显示403错误，这个不是大问题，等到我们安装博客系统的时候就会自动消失啦。到这里，我们已经能够让所有人在浏览器输入我们的域名(`blog.hk416.space`)就能访问我们的网站了。但对于一个博客系统来说，还少了一样东西——数据库。没错，我们还需要新建一个数据库！

打开你的浏览器，在地址栏输入`http://你的IP/phpMyAdmin`，输入用户名与密码(安装Oneinstack时设置的)。我们会看到这样的画面。

![phpMyAdmin主界面](https://cdn.exia.xyz/img/imouto/course7/6.png)

聪明的你一定发现了，左侧的侧边栏有一个新建选项。没错，那确实是一个可以新建数据库的地方。不过出于安全考虑，我们选择上方的`账户`，新建一个子用户。

![安全第一条](https://cdn.exia.xyz/img/imouto/course7/7.png)

![](https://cdn.exia.xyz/img/imouto/course7/8.png)

只需要填写红框中的字段就可以了，记得勾上`创建与用户同名的数据库并授予所有权限。 `这个选项。完成这一步之后呢，我们就可以避免直接使用root账户连接数据库而造成一些潜在的安全隐患，毕竟这个账号只能操作这一个数据库。

到这里网站的添加就完成啦！是不是还不错呢？



### 宝塔

宝塔就简单的多啦，在宝塔的首页，我们点击左侧栏的`网站`，然后选择`添加站点`。

![方便の宝塔](https://cdn.exia.xyz/img/imouto/course7/9.png)

按照提示添加就好了

![添加](https://cdn.exia.xyz/img/imouto/course7/10.png)

数据库字符集这里我们可以选择适用性更加广的`utf8mb4`，以满足日后日益增加的需求。点击提交，然后我们的网站这里就会多一条啦。

![](https://cdn.exia.xyz/img/imouto/course7/11.png)

其实到这里我们已经基本完成了，不过我们还要精益求精，为我们的网站加上个`https`。宝塔也是相当方便，直接点击那个橙色的`未部署`按钮，选择`Let's Encrypt`就可以自动部署了。

![](https://cdn.exia.xyz/img/imouto/course7/12.png)

![成功](https://cdn.exia.xyz/img/imouto/course7/13.png)

记得把强制https点上噢。

![大功告成](https://cdn.exia.xyz/img/imouto/course7/14.png)



