# Mission 3 Start Learning Basic!(2) #
---------------------------------------------------------
下面内容将是对M2内容的继续补充，同样只将给出简单的内容，具体内容都将附于链接，请大家继续加油，冲冲冲！<br>
## 用户输入： ##
具体代码如下：

    input（'文本内容'）
    #输出结果
    >文本内容 （用户输入部分）

输入输出格式控制：<br>
[https://www.runoob.com/python3/python3-inputoutput.html](https://www.runoob.com/python3/python3-inputoutput.html)
[https://www.liaoxuefeng.com/wiki/1016959663602400/1017032074151456](https://www.liaoxuefeng.com/wiki/1016959663602400/1017032074151456)

## 导入模块 ##
Python很重要的一部分就是利用别人已经写好的各种模块，合理运用各种模块可以达成各种你想要的效果。
具体代码如下：

    import 模块名
    #又或者导入模块中某一特定成员
    from 模块 import 特定成员

导入模块详解：<br>
[https://www.runoob.com/python3/python3-module.html](https://www.runoob.com/python3/python3-module.html)
[https://www.liaoxuefeng.com/wiki/1016959663602400/1017454145014176](https://www.liaoxuefeng.com/wiki/1016959663602400/1017454145014176)

## 条件、循环、遍历 ##
- 条件控制<br>
这里可以类比C语言学习，缩进是最重要的，直接上代码：

	    if （a>b）:	#大小比较判断
	   		statement_block_1
	    elif a in c:	#判断c的元素是否有a
	    	statement_block_2
	    else a not in d:	#判断d的元素是不是没有a
	    	statement_block_3

- 循环语句<br>
主要有for 和 while两种，没有do...while循环。<br>
while和for主要问题是注意冒号和缩进，且在Python之中，while可以和else搭配使用。

		while <expr>:	#条件成立进入while
	    	<statement(s)>
		else:	#while条件不成立进入else
	    	<additional_statement(s)>

- 遍历数字序列
	
		#range中从左到右参数分别为数头，数尾，每次增量。
		>>>for i in range(0, 10, 3) :
    	print(i)
  		
		0
		3
		6
		9
		>>>


此专题详细内容：<br>
[https://www.runoob.com/python3/python3-conditional-statements.html](https://www.runoob.com/python3/python3-conditional-statements.html)
[https://www.runoob.com/python3/python3-loop.html](https://www.runoob.com/python3/python3-loop.html)
[https://www.liaoxuefeng.com/wiki/1016959663602400/1017063413904832](https://www.liaoxuefeng.com/wiki/1016959663602400/1017063413904832)

## 关于迭代器与生成器 ##
此专题只需了解，迭代器和生成器是用于自动遍历的好工具，想深入学习 的可以在此查看：<br>
[https://www.runoob.com/python3/python3-iterator-generator.html](https://www.runoob.com/python3/python3-iterator-generator.html)
[https://www.liaoxuefeng.com/wiki/1016959663602400/1017269809315232](https://www.liaoxuefeng.com/wiki/1016959663602400/1017269809315232)
