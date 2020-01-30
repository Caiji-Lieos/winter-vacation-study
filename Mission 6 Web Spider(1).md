# Mission 6 Web Spider(1) #
-----------------------------------------------------
## 爬虫简介 ##
相信日常大家都有通过浏览器的上网的经历吧，可你们有了解过你们浏览网页的这一过程是怎么实现的嘛，如果有那么恭喜你已经掌握了学习爬虫的第一把钥匙，如果没有也没有关系，下面将会对此简要讲解。<br>
在我们使用浏览器输入一个网址的时候，敲击回车进入就能看到网站的页面信息。这个过程其实是浏览器在你敲击回车的时候**向网站服务器发送了一个请求并得到了响应，获取到了资源**。那么爬虫也就可以理解为模拟浏览器发送请求获取网页资源的这一过程，然后我们从中提取到我们想要的信息。<br>
通常爬虫爬取的页面都是**从一个页面开始，然后通过某些特定的规律在爬取完当前页面之后继续取爬取下一页面**，就这样不停的爬出所有我们想要的页面，我们也可以看出网络爬虫就是一个不停爬取网页抓取信息的程序。

## 爬虫的基本流程 ##



1. 发送请求<br>
模拟浏览器通过http库向网站服务器发起请求，即发送一个Request，一个请求里面将可以包含headers（浏览器型号等）等信息，然后等待服务器响应。这个过程有点像我们打开浏览器然后输入一个网址点击回车一样，其实这个过程就是在**模拟浏览器的环境向网站服务器发出了一次请求**。


1. 获取响应内容<br>
既然请求是Request，那么响应也有一个对应的名词，叫做Response。在我们做完上述的过程之后，若网站服务器能够正常响应，那么我们会得到一个Response，**Response的内容包括了Html、Css、JavaScript、Json字符串、二进制数据（图片或者视频）等类型，而我们想要获取到的东西就在这里面**。


1. 解析内容<br>
得到的内容可能是HTML，可以用**正则表达式**（一种寻找特定关键部分或关键字的一种手段），**网页解析库**进行解析。也可能是Json，可以直接转为 **Json对象解析**。还可能是二进制数据，可以直接保存或者做进一步的处理，这一部相当于浏览器把服务器端的文件获取到本地（Response），然后再进行解释并展现出来。


1. 保存数据<br>
保存的方式有很多，可以把数据保存为文本，也可以保存到数据库，或者（二进制数据）保存为特定的jpg、mp4等格式的文件。这就相当于我们在用浏览器浏览网页的时候，下载了网页上的图片或者视频。

好啦，了解完这些相信你对网络爬虫的原理已经有了一个大概的认知，可上面说的几个步骤又要怎么去实现他们呢。首先，我就先从Request（请求）讲起。

## Request ##
Request就是浏览器发送一个请求到网站服务器的过程，因为其主要建立于HTTP协议，因此也称为HTTP Request。<br>
一个Request可以包含的东西可不少：


- 请求方式：请求方式主要类型有GET、OST两种，另外还有HEAD、PUT、DELETE等。<br>
**GET请求的请求参数会在显示在URL（网址）链接的后面**，而比如我们用百度搜索“计算机维护队”，那么URL将为https://www.baidu.com/s?ie=UTF-8&wd=%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BB%B4%E6%8A%A4%E9%98%9F ,其中wd=后面的转义之后其实就是计算机维护队。<br>
**POST请求的请求参数会放在Request内但不会直接出现在URL链接里面**，比如在网站登陆的时候，输入用户名和密码，我们能在浏览器开发者工具中的Network页，Request请求中有Form Data的键值对信息，那里就存放了我们的登陆信息，能够有效的保户我们的账户信息安全;


- 请求URL：全称是统一资源定位符，**俗称网址**。一张图片或者一个音乐文件都可以用唯一URL来确定，它包含的信息指出文件的位置以及浏览应该怎么去处理它;


- 请求头（Request Headers）:请求头包含请求时的头信息，可包含User-Agent（指定浏览器请求头），Host，Cookies等信息;
请求体：是请求额外携带的数据，比如登陆信息等。

## Response ##
Response就是在我们向网站服务器发送请求之后，网站服务器解析了请求并作出相应的处理，最后把信息返回给我们，这个过程就叫做HTTP Response。<br>
而一个Response主要包括了：


- **响应状态：有多种，比如200(成功)，301(跳转页面)，404(找不到页面)，502(服务器错误)等;**


- 响应头(Response Headers)：比如内容类型，内容长度，服务器信息是，设置Cookie等;


- 响应体：主要包含了返回网页的代码，比如HTML,CSS,JavaScript，图片二进制等。

## 实战模拟 ##
那么现在介绍完了Request和Response之后，是不是想要赶紧尝试一下自己模拟这些过程呢。不要着急，现在就进入代码演示正题！<br>
首先我们需要先给python安装好request库。这里只简单列举一种方法，想了解**更多的安装库的方法**可参考此处：[https://www.cnblogs.com/xiohao/p/11287810.html](https://www.cnblogs.com/xiohao/p/11287810.html)

常用的安装库的方法为**在cmd窗口(命令提示符)**中输入：

	pip install request(库名)

若成功进入下载，则会显示出一条进度条表明当前下载进度，当下载100%将自动安装，安装成功之后将显示**“Successfully installed”**字样。<br>
在此也提供更多的pip操作指引：<br>[https://www.runoob.com/w3cnote/python-pip-install-usage.html](https://www.runoob.com/w3cnote/python-pip-install-usage.html)

在成功安装好request库之后，接下来开始进行实际打码操作：

	import requests # 导入requests库，需要安装
	 
	# 模拟成浏览器访问的头
	headers = {'User-Agent':'Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36'}
	resp = requests.get('https://www.baidu.com',headers=headers)
	print(resp.text) # 打印出网页源代码
	print(resp.status_code) # 打印出状态码

**很容易看出，这里我们首先是导入了request模块(第一行)，然后给headers人为写了一个浏览器访问头，而后对一个网站使用了request库中的get，并将得到的东西存进了resp变量里，而后再将其中的不同内容打印出来。这里就基本实现了模拟浏览器，发送请求，获取相应的大概过程**，你可以尝试着去请求任何网站，看看得到的东西里面都有些什么。


## 补充资料 ##


- 有关request和response的更多事情：<br>[https://www.cnblogs.com/xinz-study/p/9294452.html](https://www.cnblogs.com/xinz-study/p/9294452.html)


- 爬虫根本原理HTTP协议：<br>[https://www.cnblogs.com/an-wen/p/11180076.html](https://www.cnblogs.com/an-wen/p/11180076.html)



- request库详解：<br>[https://www.jianshu.com/p/09f78fce3739](https://www.jianshu.com/p/09f78fce3739)
