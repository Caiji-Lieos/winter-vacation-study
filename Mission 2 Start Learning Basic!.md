# Mission 2 Start Learning basic! #
-----------------------------------------------------
##  编码问题： ##
在python使用中文的时候可能会出现乱码的问题，这是因为python中默认的编码格式是ASCCII格式，在没修改在没修改编码格式时无法正确打印汉字，所以在读取中文时会报错。<br>
**解决方法：在文件开头加入 **# -*- coding: UTF-8 -*- 或者 # coding=utf-8**<br>
链接：（[https://www.runoob.com/python/python-chinese-encoding.html](https://www.runoob.com/python/python-chinese-encoding.html)）

## 基础语法： ##
- *python标识符<br>
	1. 在 Python 里，标识符由字母、数字、下划线组成。<br>
	1. 在 Python 中，所有标识符可以包括英文、数字以及下划线(_)，但不能以数字开头。<br>
	1. Python 中的标识符是区分大小写的。<br>
	1. 以下划线开头的标识符是有特殊意义的。以单下划线开头 _foo 的代表不能直接访问的类属性，需通过类提供的接口进行访问，不能用 from xxx import * 而导入。<br>
	1. 以双下划线开头的 __foo 代表类的私有成员，以双下划线开头和结尾的 __foo__ 代表 Python 里特殊方法专用的标识，如 __init__() 代表类的构造函数。<br>
	1. Python 可以同一行显示多条语句，方法是用分号“;”分开。
	
<br>

- 行和缩进（重点）<br>
	1. Python 与其他语言最大的区别就是，Python 的代码块不使用大括号 {} 来控制类，函数以及其他逻辑判断。python 最具特色的就是用缩进来写模块。<br>
	1. 缩进的空白数量是可变的，但是所有代码块语句必须包含相同的缩进空白数量（4个空格），这个必须严格执行。
        
		    #实例1
    		if True:
    			print ("True")
       	 	else:
    		print ("False")//此处缩进错误
    		# 没有严格缩进，在执行时会报错

<br>

- *多行语句<br>
	1. 但是我们可以使用斜杠（\）将一行的语句分为多行显示。
	1. 语句中包含 [], {} 或 () 括号就不需要使用多行连接符。

<br>

- *引号<br>
	1. 可以使用引号( ' )、双引号( " )、三引号( ''' 或 """ ) 来表示字符串，引号的开始与结束必须的相同类型的。
	1. 其中三引号可以由多行组成，编写多行文本的快捷语法，常用于文档字符串，在文件的特定地点，被当做注释。

<br>

- 注释（重点）<br>
	1. 单行注释采用 # 开头。
	1. 多行注释使用三个单引号(''')或三个双引号(""")。

		    #!/usr/bin/python3
		    # 第一个注释
		    # 第二个注释
		     
		    '''
		    第三注释
		    第四注释
		    '''
		     
		    """
		    第五注释
		    第六注释
		    """
<br>

- print 输出(重点)<br>
print 默认输出是换行的，如果要实现不换行需要在print参数里面添加end=''。

        #!/usr/bin/python
	    # -*- coding: UTF-8 -*-
	    
	    x="a"
	    y="b"
	    # 换行输出
	    print x
	    print y
	    
	    print '---------'
	    # 不换行输出
	    print x,
	    print y,
	    
	    # 不换行输出
	    print x,y
		
		输出结果：
		> a
		> b
		> ---------
		> a b a b

基础语法学习可参考网站（不一定用下列的自己有就看自己的）：



- 中国大学慕课MOOC python语言程序设计（网课）
[https://www.icourse163.org/learn/BIT-268001#/learn/announce](https://www.icourse163.org/learn/BIT-268001#/learn/announce)


- 菜鸟runboob python基础教程： 
[https://www.runoob.com/python3/python3-basic-syntax.html](https://www.runoob.com/python3/python3-basic-syntax.html)


- 廖雪峰笔记python教程：
[https://www.liaoxuefeng.com/wiki/1016959663602400](https://www.liaoxuefeng.com/wiki/1016959663602400)

## 本次任务小结： ##
要求**学会并掌握python以上的基础语法**，此任务要求在**2天**内看完，将要求**每天晚上qq或微信私聊彤彤或者威龙汇报进度**。
