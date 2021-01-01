终于到了最后一步，安装博客程序。前面已经介绍过了不同的博客程序，这里我们举两个最有代表性的`typecho`和`wordpress`来举个栗子。

### 1.下载博客程序

来到对应博客系统的官网->[typecho](https://typecho.org/)，[wordpress](https://wordpress.org/download/)。

不过需要注意，wordpress的官网在大陆访问奇慢无比，可能需要借助一些科学手段。没有条件的同学可以直接点这个[链接](https://mofile.own-cloud.cn/#/s/3k4vcy)，我这里提供一份`5.5.1`版本的wordpress以便没有t的同学下载。

![俩博客程序](https://cdn.exia.xyz/img/imouto/course8/sshot-1.png)

下载下来我们得到的是包含博客源码的压缩文件。但从压缩包体积来看两者的不同就体现出来了。但不是说谁文件大谁就好，轻量有轻量的优势，wordpress也有别人无法企及的功能性的优势。下一步就是将压缩包上传到服务器了。



### 2.1安装Wordpress

将我们的wordpress压缩文件上传至网站目录。在哪里上传？以宝塔为例，点击左侧**网站**选项，找到根目录点进去。

![](https://cdn.exia.xyz/img/imouto/course8/sshot-2.png)

![](https://cdn.exia.xyz/img/imouto/course8/sshot-3.png)

这里就是你的网站的根目录了，我们点击上传，将我们的Wordpress压缩包上传上去，顺便将它自带的`404.html`和`index.html`删掉。当我们把鼠标移到压缩包上面时，那一列的右侧会出现一系列的选项，我们选择把它解压。

![解压](https://cdn.exia.xyz/img/imouto/course8/sshot-4.png)

解压完成后会发现，我们根目录下会多出一个wordpress的文件夹，我们进去把所有文件移出来。不然的话你就得用`https://你的域名/wordpress`来访问你的网站了。移出来之后，我们还可以顺手把压缩包和原本wordpress这个空文件夹给删了。

好了！现在我们访问我们的域名。

![好耶！](https://cdn.exia.xyz/img/imouto/course8/sshot-5.png)

现在我们就可以开始配置安装了。选择到中文(在最下面)进行下一步。会先看到一个简单的介绍，然后我们点击**现在就开始！**进行下一步操作。

![数据库连接](https://cdn.exia.xyz/img/imouto/course8/sshot-6.png)

数据库密码用户名是什么呢？我们回到宝塔，左侧点击**数据库**就可以看到啦。

![数据库信息](https://cdn.exia.xyz/img/imouto/course8/sshot-7.png)

我们将信息填到wordpress里面，这里需要注意的是

我们只需要填写`数据库名`、`用户名`、`密码`三项即可，数据库主机正常情况下都是localhost。而最后一项前缀则是允许你**自定义**的，但是不要太长了。如果信息没有出错的话，提交之后就可以开始自动安装了。

![安装！](https://cdn.exia.xyz/img/imouto/course8/sshot-9.png)

![自由发挥时间](https://cdn.exia.xyz/img/imouto/course8/sshot-8.png)

这里就是自由发挥时间惹，填写完后，点击安装wordpress。至此，你的wordpress博客就安装完成啦！

![](https://cdn.exia.xyz/img/imouto/course8/sshot-10.png)





### 2.2 安装typecho

还是一样的步骤，将压缩包上传至根目录，解压之后发现多出来个`bulit`文件夹，还是老样子，全部移出来之后删掉原本的bulit文件夹。打开浏览器访问你的域名。

![yo](https://cdn.exia.xyz/img/imouto/course8/sshot-11.png)

也是差不多的界面，我们按照引导来走。

![配置](https://cdn.exia.xyz/img/imouto/course8/sshot-12.png)

一样的，我们只需要填写`数据库名`、`用户名`、`密码`三项即可，数据库主机正常情况下都是localhost，端口一般都是3306，前缀也可以自定义。而第一项数据库适配器则是他自动匹配的，无需选择。接着在下面创建管理员账号这里填写你的自定义的信息就完成了。

![安装成功！](https://cdn.exia.xyz/img/imouto/course8/sshot-13.png)

**不过还没结束！**我们还需要回到网站根目录，将`install`文件夹与`install.php`删除，以绝后患。到这里，typecho的搭建才算真正的完成了。

### 3.完结

到这里，搭建博客的教学系列基本完成了，接下来会时不时更新一些相关的技巧与资源。祝大家的博客之路一路顺风！