> 使用虚拟主机的玩家可以跳过这一章节

在搭建网站之前，我们需要知道的是，目前大多数的服务器都是使用Linux系统。简单理解一下Linux是什么，Linux就是一种没有桌面的系统(还是个别版本会有)，我们一般只能通过输入命令来使用它。它相比于Windows在服务器上的优势是，它系统本身占用的资源非常少，一个1h512mb的Linux服务器可以妥妥地运行几个网站；然而同等配置的Windows服务器系统自己可能就占了大部分内存资源，这是十分不划算的。这使得Linux在服务器领域相当吃香(原因远不仅如此)。



这将是我们以后经常要打交道的东西，所以我们还是要尽量掌握它，毕竟它也不难。首先，我们需要连接上你的服务器

### 工具

工欲善其事，必先利其器。我们一般通过`SSH协议`与我们的服务器进行连接，而SSH需要一些软件支持。例如`XShell`，`FinalShell`。这里我将使用`XShell`来进行教学。各个SSH软件的使用方法都是大同小异的，无需担心。

打开XShell，可以看到如下界面

![](https://cdn.exia.xyz/img/imouto/course4/linux1.jpg)

这个时候我们点击左上角的文件夹（📂）图标，`新建连接`(会话)，可以看到如下界面。

![](https://cdn.exia.xyz/img/imouto/course4/linux2.jpg)

这里可以按照以下指示填写

> 名称 -> 随便起名
>
> 协议 -> 默认SSH
>
> 主机 -> 你的服务器IP地址
>
> 端口号 -> 默认22
>
> 说明 -> 随意，可留空

接下来再点击左侧树状栏的`用户身份验证`一项，填写你的用户名(一般为`root`)与密码

![](https://cdn.exia.xyz/img/imouto/course4/linux3.jpg)

再点击连接即可，期间可能会弹出关于**主机密钥**的弹窗，点击“一次性保存”即可。连接之后，就可以看到一个跳动的光标在等着你辣。

![](https://cdn.exia.xyz/img/imouto/course4/linux4.jpg)

### 界面

没错，这就是你的操作空间，枯燥而乏味的命令行。当然，不同的Linux版本在界面方面会有些许不同。但大体是一样的，不必担心作者使用的Linux版本与你不一样而引发一些问题。如果有区别的话，我在文中指出的。



### 基本指令

#### ls指令

功能：列出当前目录下的内容

![](https://cdn.exia.xyz/img/imouto/course4/linux5.jpg)

#### cd指令

功能：前往指定目录。

这里有一些指定写法在这里列举一下。

```bash
#格式
#cd+空格+(绝对路径/相对路径)

#返回上一级
cd ..

#返回上一级的某一文件夹(假设为home)
cd ../home

#返回根目录
cd /

#前往指定路径
cd /home/soft/xxx
```

从上面的例子可以知道两个英文的点（`..`）就是上一级。什么是绝对路径呢？绝对路径就是从你的服务器根目录到指定文件夹的路径，相对应的，相对路径就是目标文件夹相对于你当前所处位置的路径。打个比方，现在有三个文件夹ABC。其中C文件位于B文件夹中，而B文件夹位于A文件夹中。而**A直接处于根目录中**。

![](https://cdn.exia.xyz/img/imouto/course4/cd1.png)

**我们现在处于A文件夹**，我们想要到达文件夹C有几种方式呢？

```shell
#方法一：绝对路径
cd /A/B/C

#方法二：相对路径
cd B/C
```

聪明的你应该发现了，一般绝对路径是以`/`起头的，而相对路径则没有。

再举个例子，**假设我们现在处于C文件夹中**，我们想要到达文件夹A有几种方法呢？

```shell
#方法一：绝对路径
cd /A

#方法二：相对路径
cd ../..
```

欸嘿！是不是很神奇。



#### mkdir指令

功能：建立文件夹

```shell
#在当前目录建立hi文件夹
mkdir hi

#在指定路径(/root/jojo)建立文件夹(jostar)
mkdir /root/jojo/jostar
```



#### 其他常用指令

因为网上有比较完善的教程了，我就不重复写了，这里[贴出来](https://www.runoob.com/linux/linux-command-manual.html)可以去看一下。不用掌握太多，但至少掌握[`cp`](https://www.runoob.com/linux/linux-comm-cp.html)，[`mv`](https://www.runoob.com/linux/linux-comm-mv.html)，[`zip`](https://www.runoob.com/linux/linux-comm-zip.html)，[`vi`](https://www.runoob.com/linux/linux-vim.html)，`wget`，[`rm`](https://www.runoob.com/linux/linux-comm-rm.html)指令。

~~我才不是偷懒呢~~



### 附加课

有些时候我们常常会因为某些原因被迫突然与服务器中断连接。如果当时我们正在安装某程序或者编译一些东西的时候，该进程就会被打断，直接莫得了，这是非常难受的。再例如有些时候安装一个网站环境可能要个把钟，我们需要让他自己在后台跑怎么办呢？

当当当，隆重介绍`screen`

我们可以使用`screen -S 会话名`指令来新建一个窗口。当我们想让他后台运行时按`ctrl+a+d`即可返回原始窗口。当我们想看看进程时，可以使用`screen -r 会话名`重新连接回去。

使用场景：中午11：30，网络条件不好的王花花同学连上了服务器，打算搭建一下网站环境

```shell
#首先新建一个窗口(install)
screen -S install

#开始搭建
...

#牙白！这个时候网断了，王花花同学切换成了5G重新连接服务器，并重新访问install窗口
screen -r install

#还在默默安装...
...

#喜玛达！要吃饭了，王花花同学主动断开连接，程序转为后台运行
`ctrl+a+d`
```

由此可见，screen确实是十分的方便。不过有些用户可能会出现提示`command not found`提示，这是因为系统本身没有自带screen功能。那就需要我们自己安装了。

```shell
#centos执行
yum install screen

#debian执行
apt-get install screen
```



### 结束

至此，相信你已经能稍微使用一下Linux系统了，刚开始上手可能会有些不适应，但是一定要多加练习，迎难而上，这样你的问题很快就能解决了。



