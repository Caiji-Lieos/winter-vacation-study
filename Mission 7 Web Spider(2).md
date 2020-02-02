# Mission 7 Web Spider(2) #
-------------------------------------------------------
## 回顾 ##
在上一个mission之中，我们已经简单介绍了爬虫的基本原理，还演示了简单爬虫中最常用到的请求方式：通过使用request库中的get发送一个请求并得到一个响应。我们还自己构造了请求中的headers...<br>
总的来说目前**已经介绍了request库中的get函数还有其中的一个参数headers**，但这很明显只是冰山的一角。那么现在，让我们将继续去揭示request的更多用法吧。

## 各种请求方式 ##
前面我们提到发送的请求可以是带有不同的目的性的，比如得到的get，发送的post，删除的delete等等。在request库中，也就包含了这么多种请求的方式。

		import requests
		 
		requests.get('http://httpbin.org/get') # 发送get请求
		requests.post('http://httpbin.org/post') # 发送post请求，只要调用post方法，传入一个url参数
		requests.put('http://httpbin.org/put')
		requests.delete('http://httpbin.org/delete')

## 请求 ##
1. 基本get<br>
	
		import requests
		 
		resp = requests.get('http://httpbin.org/get')
		print(resp.text)

1. get的参数<br>

		import requests
		data = {
		    "name":"zhaofan",
		    "age":22
		}
		response = requests.get("http://httpbin.org/get",params=data)#需要在此让params参数等于我们写好的字典集
		#上面的效果等价于
		#response = requests.get("http://httpbin.org/get?name=zhaofan&age=23")

	上面展示了**request允许通过params参数传递一个字典内容而后直接制造一个URL**。若params的字典内容为None则不会添加到URL之中。

1. 解析JSON<br>

	Json是一种网页中用来交换显示数据常用的语言，也可说是一种数据格式。在资讯类数据类网站中经常能见到。

		import requests
		import json
		 
		resp = requests.get('http://httpbin.org/get')
		#print(resp.text)
		print(resp.json())#直接把get回来的内容.json()即可解析
		#print(json.loads(resp.text))
		#print(type(resp.json()))

	对于JSON的解析是一门专门的学问，解析得当可以更快的从中获取自己想要的东西，感兴趣的同学可以自己去查查了解，这里只简单介绍并不铺开。

1. 获取二进制数据<br>

	二进制一般是为了保存图片的。当然也还有其他可通过二进制保存的也会用到。

		import requests
		 
		resp = requests.get('http://www.baidu.com/img/baidu_jgylogo3.gif')
		print(resp.content)#想获取二进制那就将响应.content()即可

	比如你想保存一张图片，**你找到了图片的URL，获得了图片的响应，然后你保存了其二进制文件，那么只需要最后把文件后缀改成对应的格式即可打开**。

1. 添加headers

		import requests
		 
		headers = {'User-Agent':'Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36'}
		resp = requests.get('http://www.baidu.com', headers=headers)

	**有些网页不接受python直接去请求，他们会检查请求对象是否为浏览器**，如果没有对应的浏览器头信息就会阻止我们的访问导致爬虫无法连接，这时候我们就应该给我们的**请求中添加一个headers来伪装成浏览器访问**。那么怎么知道自己浏览器的headers呢？其实很简单：
	- 首先在电脑上随便打开一个浏览器。
	- 按F12或者右键打开审查元素。
	- 找到Network，根据提示ctrl+R刷新随便点击一个文件，在右侧即可找到当前浏览器headers。
	- 我们只需要利用其中的User-Agent信息即可。

## 基本post ##

	import requests
	 
	data = {
	    'name' : 'jack',
	    'age' : 20
	}
	resp = requests.post('http://httpbin.org/post', data=data)

一个POST必然是要有一个Form Data的表单提交的，我们只要把信息传给data参数就可以了。一个POST请求只需要调用post方法，是不是特别方便呢。如果不觉得方便的话，可以去参考urllib的使用方法。

## 小结 ##
**在这里又给大家介绍了一些有关于request的更多用法，下一次我们会更进一步讲一些更高级的用法。<br>
趁着这突如其来的小长假，继续加油加油！
还请一定按时间在q群里面报道噢！
另外想说的是已经有能力的同学其实可以试着自己去模仿别人的爬虫打打，也可以去问问浩辉队长了解更高级的爬虫用法，不用害羞的，我们队长又不会咬人哈哈哈。**

## 本文参考 ##
- [https://www.jqhtml.com/13264.html](https://www.jqhtml.com/13264.html)
- [https://www.cnblogs.com/xinz-study/p/9294452.html](https://www.cnblogs.com/xinz-study/p/9294452.html)
