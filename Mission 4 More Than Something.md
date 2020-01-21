# Mission 4 More Than Something #
---------------------------------------------------------
## 基本数据类型：##
(在此对内容都只做简单介绍，具体内容可在以下链接查看)
[https://www.runoob.com/python3/python3-data-type.html](https://www.runoob.com/python3/python3-data-type.html)


1. 定义变量：<br>
直接 （一个变量名 = 一个值），值可以直接是整型数、浮点型数、布尔数和字符串。

1. 多个变量赋值：<br>
直接同时多个连等于
赋值号（=）左右两边分别将变量和值用逗号分隔开，这样将会一一对应赋值。

1. 标准数据类型：<br>
	- Python3中又六个标准数据类型：Number、String、List、Tuple、Set、Dictionary。
	- 其中Number、String、Tuple是不可变数据，其他3中数据类型都是可变数据类型。
	- （不可变数据类型： 当该数据类型的对应变量的值发生了改变，那么它对应的内存地址也会发生改变，对于这种数据类型，就称不可变数据类型。
	- 可变数据类型    ：当该数据类型的对应变量的值发生了改变，那么它对应的内存地址不发生改变，对于这种数据类型，就称可变数据类型。）

1. Number(数字)：
	- 数字支持int、float、bool、complex（复数）。
	- 用type（）可查询变量所指向得对象类型。
	- 也可用isinstance（变量，类型）来判断这个变量是不是这个类型。
	- isinstance 和 type 的区别在于（涉及到类的继承不要求一定弄懂）：
		- type()不会认为子类是一种父类类型。
		- isinstance()会认为子类是一种父类类型。
		- 可以通过使用del语句删除单个或多个对象。

	- 数值运算中注意的点：
		- 数值的除法包含两个运算符：/ 返回一个浮点数，// 返回一个整数。
		- 在混合计算时，Python会把整型转换成为浮点数。
		- Python还支持复数，复数由实数部分和虚数部分构成，可以用a + bj,或者complex(a,b)表示， 复数的实部a和虚部b都是浮点型。


1. String（字符串）
	- 用'或''括起来，同时和C语言类似用反斜杠\转义特殊字符。
	- 字符串的截取重点：
		- 语法：变量[头下标：尾下表]。
		- 索引值以0为开始值，-1为从末尾的开始位置。


## 补充资料（对以上内容更详细的讲解一定要看的）： ##
1. 菜鸟教程：
	- 数字：
[https://www.runoob.com/python3/python3-number.html](https://www.runoob.com/python3/python3-number.html)
	- 字符串：
[https://www.runoob.com/python3/python3-string.html](https://www.runoob.com/python3/python3-string.html)


1. 中国大学慕课MOOC网课（第三周）：
	- [https://www.icourse163.org/learn/BIT-268001#/learn/content](https://www.icourse163.org/learn/BIT-268001#/learn/content)

1. 廖雪峰笔记
	- 数字：
[https://www.liaoxuefeng.com/wiki/1016959663602400/1017063826246112](https://www.liaoxuefeng.com/wiki/1016959663602400/1017063826246112)
	- 字符串：
[https://www.liaoxuefeng.com/wiki/1016959663602400/1017075323632896
](https://www.liaoxuefeng.com/wiki/1016959663602400/1017075323632896)

## 小结： ##
数字和字符串都是基础中的基础，之前C语言中的类型和字符串操作都比较复杂，而这些问题都在python中得到了较好的完善，所以请重视这些和C不同的地方。<br>
为让大家互相了解彼此的学习进度如何好知道目前学习进度已经到了哪个阶段，本次汇报将试行直接在群里汇报！！！<br>
有疑问的地方都欢迎来找我和彤彤！！！
各位加油欧里给！！！
