# Mission 8 Web Spider(3) #
--------------------------------------------------------
## 前文回顾 ##
在前面的内容之中我们已经介绍了request库的各种简单用法，总的来说对于一个简单爬虫最重要的地方之一在于给我们的爬虫**伪造好一个有效的headers**，并通过**request.get(url,headers = headers)**来获取到想要爬取网页的html等文件。<br>
## “一碗漂亮的汤” ##
得到这些文件之后我们知道这里面会包含有许多的东西(html,js,json...)，这些并不都是我们想要的，因此我们在获取到源响应之后要做的事情就是解析这些文件，并试图从中找到我们真正需要的东西。<br>
现如今，解析这些文件的方式已经有很多种，在这里我们将只介绍一种**BeautifulSoup（直译漂亮的汤）**。**它是一种网页解析库，可支持很多解析器，主流的包含lxml HTML解析器和python的标准库**，两者的使用方式很类似。<br>

- **安装BeautifulSoup库：（cmd中）**

		pip install BeautifulSoup4 #库名可不分大小写
		pip3 install BeautifulSoup4

- **使用库的方法：**

		from bs4 import BeautifulSoup

- **使用解析器：**

		from bs4 import BeautifulSoup
		 
		# Python的标准库
		BeautifulSoup(html, 'html.parser')
		 
		# lxml
		BeautifulSoup(html, 'lxml')

**两种解析方式的小区别：** Python内置标准库的执行速度一般，但是低版本的Python中，中文的容错能力比较差。lxmlHTML 解析器的执行速度快，但是需要安装 C语言的依赖库。

至此，前期的准备工作已经完成了，网页解析库我们已经有了，那么接下来我们还得找个东西来用这个库。

## lxml的安装 ##
由于python标准库无需安装，且lxml和标准库的使用方式大同小异，所以在这里着重以lxml为例子来介绍。

首先是安装，安装lxml是个看脸的活，运气好的可以直接用cmd的pip install一键安装即可，但有时候由于系统的原因会出现安装失败的现象，那么接下来我们来讲讲该怎么来应付：

- **直接用cmd安装lxml**

		pip install lxml
		pip3 isntall lxml

当上面直接安装的方式失败时，可以尝试下面的方法：

- **安装lxml的另一种方式：wheel安装**

	1. 先安装wheel库(cmd)：
	
			pip install wheel
			pip3 install wheel
	安装这个库之后我们才可以正常安装.whl文件，这里提供一个lxml.whl文件的下载地址：[https://pypi.python.org/pypi/lxml/3.6.0](https://pypi.python.org/pypi/lxml/3.6.0)

	1. 下载好之后找到.whl文件的位置，以管理员身份运行cmd，然后cd进.whl文件的位置。然后用下列指令安装：

			pip install .whl文件全名（这里我们安装的是lxml.whl）
			pip3 install .whl文件全名
	当显示了Seccussfully Installed字样即安装成功，也可进python使用检查。



- 若是上面的方法都不适合你，可以考虑**直接安装集成了python的anaconda**，这个软件安装库会比原生python容易许多，也有很多自带的库在其中。

## BeautifulSoup的基本标签选择方法 ##
讲完了安装，接下来就来讲讲怎么具体使用BeautifulSoup和lxml

- 首先我们通过requests的get请求获取响应包：

		import requests
		headers = {User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.130 Safari/537.36}
		response = requests('baidu.com', headers = headers)

- 由于我们解析的是响应包里面的文本内容，因此我们需要用.text调出响应包中的文本部分：
		
		from bs4 import BeautifulSoup
		import lxml
		soup = BeautifulSoup(response.text, 'lxml')

到这里我们算是已经可以开始解析响应包里面的文本内容了，下面讲讲怎么抓出来我们想要的东西。<br>
我们知道我们分析的文本其实就是一个html文件，那么一个html里面有的是什么呢？其实就是标签，和标签里面的内容。

- **获取标签**

可以直接输入任何一个标签名获得使用了该名的所有标签：
print(soup.title) #获取所有名为title的标签
print(soup.div) #获取所有名为div的标签

- **获取名称**

		print(soup.title.name)
		print(soup.div.name)  #实际上就是标签的名字

- **获取属性**

		print(soup.p.attrs['class']) #获取<p>标签的属性
		print(soup.p['class'])	两者都能达到同一效果

- **获取内容**

		print(soup.tilte.string) #获取tilte标签里面的全部内容
		#还可以套娃
		print(soup.body.p.string)#获取body标签里面的p标签里的内容

## BeautifulSoup常见用法 ##
上面的内容我们已经介绍了几种基本的抓取标签有关信息的方法，但也能够发现上面的方法太过于简单和单一，而我们要面对的html是更加复杂的（比如有很多class、id等）。<br>
为方便人使用，索性BeautifulSoup给我们提供了很方便的标准选择器，也就是API方法，这里着重介绍2个：find()和find_all()。其他方法的参数和用法类似，大家可以举一反三。


## 标准选择器：find_all() ##

find\_all(name,attrs,recursive,text,**kwargs)可以根据标签，属性，内容查找文档。<br>
find\_all()其实和正则表达式的原理有点类似，**能根据给出的匹配模式找出所有匹配的结果，再把所有结果以列表返回**。

- **过滤器：添加一些搜索参数**

前面说到，find_all()是可以添加参数来自定义匹配类型的，添加参数来筛选就像是一个过滤的过程，find\_all()方法搜索当前标签的所有标签子节点，并判断是否符合过滤器的条件。这里有几个例子：

		soup.find_all("title")
		# [<title>The Dormouse's story</title>]
		 
		soup.find_all("p", "title")
		# [<p class="title"><b>The Dormouse's story</b></p>]
		 
		soup.find_all("a")
		# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
		#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
		#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
		 
		soup.find_all(id="link2")
		# [<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>]

有几个方法很相似,还有几个方法是新的,参数中的 string 和id是什么含义? 为什么 find\_all("p", "title") 返回的是CSS Class为”title”的标签? 我们来仔细看一下find_all()的参数:


- **name参数**

name参数可以查找到所有名字为name的标签。
	
	#得到标签名为title的所有标签
	soup.find_all("title") #name参数为title

- **keyword参数**

如果我们通过上面的name参数找到了几个同标签名的标签，但我们只想得到特定一个class属性的，我们就可以这么做：
	
	#找到tilte标签名。class属性为top的标签
	soup.find_all('tilte', class_='top')
这里有个值得注意的地方，能够看到**这里class属性我们在最后还加了一个下划线“\_”,这是因为class本身是python中标识类的一个关键词，所以在我们想使用自己表达的意思的时候就要避开关键字，因此用了class_**。<br>
keyword的参数有许多，不仅仅是class，也可以是id等属性，这些可以在自己的实践中不断地去发现。

- **limit参数**

find_all()方法返回全部的搜索结果，但有时候我们只需要一部分，这种时候我们就可以使用limit参数来帮助我们限制返回结果的数量，即当搜索到我们limit参数指定数量的内容之后便会停止搜索。
	
	#比如我们只想从所有标签中搜索出两个div标签
	soup.find_all("div", limit = 2)

<br>
这里只介绍了三种，find_all()还有其他的参数，想了解的同学可以自行百度或参考官方文档即可。

## find() ##

find_all()是返回所有元素（搜索结果），find()返回单个元素。
在参数方面，其实find()和find_all()大同小异，可以通过下列相同意义的两个句子进行对比：

	#找出一个class属性为top的div标签。
	soup.find_all('div', class_='top', limit=1)
	soup.find('div', class_='top')

两者的唯一区别是，**find_all()不论找到与否，都将返回一个列表（找不到返回空列表），而find()找到了就只返回一个结果，找不到就只返回None**。

## CSS选择器 ##

Beautiful Soup支持大部分的CSS选择器。在select()中从传入字符串参数，即可使用CSS选择器语法找到标签，其**中我们在些css时需要注意，标签class类名加"."，id属性加"#":**
	
	#通过标签逐层寻找
	soup.select("body a")#找到<body>里面的<a>
	#找到某个标签下的直接(下一级)子标签
	soup.("p > a")	#找到<p>下一级中的所有<a>
	soup.("p > #link1") #找到<p>下一级中id为link1的<a>
	#通过class类名查找
	soup.select(".sister")
	#通过标签和id查找
	soup.select("a#link2") #找到id为link2的<a>

## 总结 ##
- BeautifulSoup解析库推荐使用lxml,但个别出现乱码的情况也可使用html.parser
- BeautifulSoup筛选标签的方式虽然仍有缺陷,但速度较快
- find和find_all是比较常用的,熟悉css的也可以根据爱好使用select
- get_text()方法获取标签文本内容,get[attrs]获取标签属性

至此,你已经基本掌握了制作一个简单爬虫所需要具备的基础知识,你可以自由地去找寻项目来动手实践,学代码的东西往往都还是多打才能多理解记得牢<br>
开学届时将会有一个作品小展示,请各位提前准备好自己的爬虫或其他pyhton有关的作品,期待哟<br>
如果在过程中遇到了什么问题,在自己尝试解决无果之后也可以来询问我和彤彤师姐,或者浩珲师兄也行,随时都欢迎打扰、撩骚

















